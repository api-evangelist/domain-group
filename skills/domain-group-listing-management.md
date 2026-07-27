---
name: Upload and manage listings on Domain from a CRM
description: >-
  The broker-authorised write path - upsert residential, commercial, business and
  off-market listings, poll the processing report, and read back enquiries and
  performance statistics.
api: openapi/domain-group-openapi-latest.json
operations:
  - Listings_UpsertResidentialListing
  - listings_upsertcommerciallisting
  - Listings_UpsertBusinessListing
  - listings_upsertresidentialoffmarket
  - listings_upsertcommercialoffmarket
  - listings_upsertbusinessoffmarket
  - Listings_GetListingReport
  - Listings_GetListingReportByReference
  - Listings_Get
  - Listings_GetEnquiries
  - Listings_GetListingStatistics
  - Agencies_CreateTestAgency
  - Me_GetMyAgencies
scopes:
  - api_listings_write
  - api_listings_read
  - api_agencies_write
  - api_enquiries_read
generated: '2026-07-26'
method: generated
source: openapi/domain-group-openapi-latest.json + https://developer.domain.com.au/docs/latest/apis/pkg_listing_management
---

# Upload and manage listings on Domain from a CRM

This is the surface Australian agency CRM software integrates with. It is the
**most gated** part of Domain: the read APIs are self-serve, this one is not.

## Access gate — read this first

1. Add the **Listings Management** package to a project in its **Sandbox**
   variant.
2. Build and test entirely against `https://api.domain.com.au/sandbox/`.
3. Complete Domain's testing and sign-off process by email to
   **api@domain.com.au**.
4. Obtain **written permission from the principal agent** of every agency whose
   listings you will manage — see
   https://developer.domain.com.au/docs/latest/apis/pkg_listing_management/guides/agency-authorisation
5. Only then create a Production project (recommended) or switch the sandbox
   project's package to Production.

Scopes: `api_listings_write` (plus `api_listings_read` to verify,
`api_agencies_write` for test agencies, `api_enquiries_read` for lead readback).

## Steps

1. **Set up a sandbox agency.** `Agencies_CreateTestAgency`
   (`POST /v1/agencies/_testAgency`) creates a throwaway agency to publish
   against. **Sandbox data is wiped every Sunday** — re-create your test
   agencies and listings weekly and never hard-code sandbox ids.

2. **Confirm your authorisation.** `Me_GetMyAgencies` (`GET /v1/me/agencies`)
   confirms which agencies the authenticated user may act for.

3. **Upsert the listing.** These are `PUT`/`POST` *upserts* keyed on your own
   agency reference, not create-then-update pairs:
   - `Listings_UpsertResidentialListing` — `PUT /v1/listings/residential`
   - `listings_upsertcommerciallisting` — `PUT /v2/listings/commercial`
   - `Listings_UpsertBusinessListing` — `PUT /v1/listings/business`

   Off-market variants:
   - `listings_upsertresidentialoffmarket` — `POST /v2/listings/residential/offmarket`
   - `listings_upsertcommercialoffmarket` — `POST /v2/listings/commercial/offmarket`
   - `listings_upsertbusinessoffmarket` — `POST /v2/listings/business/offmarket`

   Upload is asynchronous — expect `202 Accepted` rather than the finished
   listing.

4. **Poll the processing report.** `Listings_GetListingReportByReference`
   (`GET /v1/listings/processingReports`) by your own reference, or
   `Listings_GetListingReport` (`GET /v1/listings/processingReports/{id}`) by
   report id. **Do not assume a 2xx on the upsert means the listing went live** —
   the report is where validation failures surface.

   Better: subscribe to the `listingProcessingReports` webhook resource type and
   let Domain push you the report id (see
   `skills/domain-group-webhook-subscriptions.md`) instead of polling.

5. **Verify and monitor.** `Listings_Get` (`GET /v1/listings/{id}`) for the live
   record, `Listings_GetEnquiries` (`GET /v1/listings/{id}/enquiries`) for leads,
   `Listings_GetListingStatistics` (`GET /v1/listings/{id}/statistics`) for
   performance.

   > Note: the v1 operations `Listings_UpdateOffmarketDetails` and
   > `Listings_GetListingStatisticsByAgentId` are flagged `deprecated: true` in
   > the v1 OpenAPI document — do not build new integrations on them.

## Rules

- **No idempotency key exists.** Domain documents none, and none of the three
  OpenAPI documents contain one. The upserts are keyed on your agency reference,
  which is what makes a retry safe — **retry the same reference, never a fresh
  one.** A new reference on retry creates a duplicate live listing.
- **Migrating from the legacy XML feed?** Domain publishes a guide at
  /docs/latest/apis/pkg_listing_management/guides/migrating-from-xml.
- **429 handling:** honour `Retry-After` and `X-Quota-Exceeded`. Bulk overnight
  syncs are exactly the workload that trips the per-day quota (reset 10am AEST).
- **401/403:** read `X-Domain-Security-Reason` first. For this package it is
  usually a missing `api_listings_write` scope, an unauthorised agency, or the
  project still being pointed at the wrong environment.
