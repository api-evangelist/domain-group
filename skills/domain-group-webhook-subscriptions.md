---
name: Subscribe to Domain webhooks and process notifications
description: >-
  Register and verify a webhook endpoint, create subscriptions for the resource
  types you care about, verify the HMAC signature on incoming batches, and
  acknowledge correctly so Domain does not disable the endpoint.
api: openapi/domain-group-openapi-latest.json
operations:
  - Webhooks_CreateSubscription
  - Webhooks_ListSubscriptions
  - Webhooks_GetSubscription
  - Webhooks_DeleteSubscription
  - Me_GetMyAgencies
  - Me_GetMyProviders
  - Listings_GetListingReport
scopes:
  - api_webhooks_write
generated: '2026-07-26'
method: generated
source: openapi/domain-group-openapi-latest.json + https://developer.domain.com.au/docs/latest/apis/pkg_webhooks
---

# Subscribe to Domain webhooks and process notifications

Webhooks are a separate API package. The endpoint itself is registered in the
portal UI; only the *subscriptions* are managed over the API.

## Before you start

- Scope: `api_webhooks_write`.
- Agency-scoped subscriptions require **user context** — a token from the
  Authorization Code flow. Client Credentials alone will fail with
  *"Authenticated without user context details. Unable to verify access to agency."*
- Your endpoint must be publicly resolvable, on a real DNS name, with a valid
  (not self-signed) TLS certificate.

## Steps

1. **Register the endpoint.** In the portal, open the project → *Webhooks* →
   *Create Webhook* → supply the URL. The webhook id is prefixed `whk_`.

2. **Pass verification.** Domain sends two `GET` requests to your URL:
   - `GET https://you.example/hook/?verification=vfy_123456` — respond **204 No Content**.
   - `GET https://you.example/hook/?verification=vfy_invalid_code` — respond **404 Not Found**.

   Your endpoint must keep answering these correctly forever, not just once.
   Then press *Verify* in the portal.

3. **Pick the owner scope.** `Me_GetMyAgencies` (`GET /v1/me/agencies`) lists the
   agency ids the logged-in user may subscribe for; `Me_GetMyProviders`
   (`GET /v1/me/providers`) lists the provider ids the client is linked to. The
   `group` owner type only accepts the owner id `public`.

4. **Create a subscription** with `Webhooks_CreateSubscription`
   (`PUT /v1/webhooks/{id}/subscriptions`), one per
   (resourceType, ownerType, ownerId) combination:

   ```json
   { "resourceType": "listings", "ownerType": "agency", "ownerId": "12345" }
   ```

   Valid `resourceType` values: `agencies`, `agents`, `enquiries`, `listings`,
   `projects`, `listingProcessingReports`, `heartbeat`. Start with `heartbeat`
   (`ownerType: group`, `ownerId: public`) to prove the pipe works — you should
   see one at least every 5 minutes.

5. **Verify with** `Webhooks_ListSubscriptions`
   (`GET /v1/webhooks/{id}/subscriptions`) or `Webhooks_GetSubscription`
   (`GET /v1/subscriptions/{id}`). Subscription ids are prefixed `subs_`.

6. **Process notifications.** Domain `POST`s a **JSON array** — always an array,
   even for a single event — to your endpoint:

   ```json
   [{ "resourceType": "enquiries",
      "resourceId": "...",
      "date": "2018-01-31T14:59:27.9479833+11:00",
      "subscriptionId": "...",
      "ownerId": "12345",
      "ownerType": "agency",
      "notificationId": "58f1cde3-ad7c-420e-8686-b94db841a930",
      "isDeleted": false }]
   ```

   a. Recompute `HMAC-SHA1(body, verificationCode)` and compare it, lowercase
      hex, against the `X-Domain-Signature` header. On mismatch, discard and
      return **404**.
   b. Push the batch onto a queue and return **204 No Content** immediately —
      ideally inside 2 seconds. **Do not process before acknowledging.** Domain
      measures your response time and disables webhooks that are consistently
      slow or erroring.
   c. Off the queue, re-read each resource by id: listings via `Listings_Get`,
      enquiries via `Enquiries_Get`, agencies via `Agencies_Get`, agents via
      `Agents_Get`, processing reports via `Listings_GetListingReport`
      (`GET /v1/listings/processingReports/{id}`). Honour `isDeleted`.

7. **Unsubscribe** with `Webhooks_DeleteSubscription`
   (`DELETE /v1/subscriptions/{id}`) → `204 No Content`.

## Rules

- Notifications are **pointers, not payloads** — they carry ids, not the changed
  record. Always re-read.
- Notifications are batched; size your handler for arrays.
- Webhook events are the only push surface Domain offers. There is no AsyncAPI
  document and no streaming API. The event catalog lives in
  `asyncapi/domain-group-webhooks.yml`.
