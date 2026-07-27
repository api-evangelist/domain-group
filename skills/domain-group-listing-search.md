---
name: Search Domain listings and enquire on one
description: >-
  Run a residential, commercial or business listing search across
  domain.com.au, page through the results correctly, pull the full listing and
  its agency/agent, and submit an enquiry.
api: openapi/domain-group-openapi-latest.json
operations:
  - Listings_ResidentialSearch
  - Listings_DetailedResidentialSearch
  - Listings_DetailedSoldResidentialSearch
  - Listings_DetailedCommercialSearch
  - Listings_DetailedBusinessSearch
  - ListingLocations_Search
  - Listings_Get
  - Agencies_Get
  - Agents_Get
  - Enquiries_Post
  - Enquiries_Get
scopes:
  - api_listings_read
  - api_agencies_read
  - api_enquiries_write
  - api_enquiries_read
generated: '2026-07-26'
method: generated
source: openapi/domain-group-openapi-latest.json + https://developer.domain.com.au/docs/latest/apis/pkg_agents_listings
---

# Search Domain listings and enquire on one

This is the surface granted automatically on signup (Agents & Listings +
Properties & Locations), so it is the fastest path to a working integration.

## Before you start

- Base URL `https://api.domain.com.au/`. JSON over HTTPS only; request and
  response bodies are camelCase.
- Scopes: `api_listings_read`, `api_agencies_read`. Submitting an enquiry needs
  `api_enquiries_write`.
- The search operations are **POST, not GET** — Domain routes read endpoints with
  many optional parameters through POST to avoid URI length limits. Pagination
  parameters therefore go in the JSON body, not the query string.

## Steps

1. **Narrow the geography first.** `ListingLocations_Search`
   (`GET /v1/listings/locations`) resolves suburb / region names to the location
   objects the search criteria expect. Searching on raw strings produces noisy
   results.

2. **Search.** Pick the operation that matches the asset class:
   - `Listings_ResidentialSearch` (`POST /v1/listingSearch/residential/search`)
     — for-sale and for-rent residential.
   - `Listings_DetailedSoldResidentialSearch`
     (`POST /v1/listingSearch/residential/searchSold`) — sold results.
   - `Listings_DetailedResidentialSearch`
     (`POST /v1/listings/residential/_search`) — the detailed residential search.
   - `Listings_DetailedCommercialSearch` (`POST /v1/listings/commercial/_search`)
     and `Listings_DetailedBusinessSearch` (`POST /v1/listings/business/_search`).

   Put `pageNumber` and `pageSize` in the POST body:
   `{"pageNumber": 1, "pageSize": 50}`. Pages start at **1**; the default page
   size is 20 and the maximum is 100. A `pageNumber` of 0 or a negative value
   silently returns page 1 — do not treat that as an error, and do not use it as
   a loop terminator.

3. **Page to the end.** Read the `X-Total-Count` response header to size the
   result set. **It is not always present**: when Domain cannot produce a
   reliable count the header is omitted and pages past the last one come back
   empty. Terminate on an empty page, not only on a count.

4. **Fetch the detail.** `Listings_Get` (`GET /v1/listings/{id}`) for the full
   listing record.

5. **Resolve who is selling it.** `Agencies_Get` (`GET /v1/agencies/{id}`) and
   `Agents_Get` (`GET /v1/agents/{id}`) for the agency and agent behind the
   listing. `Agencies_GetListings` and `Agents_GetListings` walk the other way.

6. **Enquire.** `Enquiries_Post` (`POST /v1/enquiries`) submits an enquiry
   against a listing; `Enquiries_Get` (`GET /v1/enquiries/{id}`) reads one back.
   Requires `api_enquiries_write`.

## Rules

- **No idempotency.** Domain documents no idempotency key and none of the three
  OpenAPI documents contain one. `Enquiries_Post` is a real side effect —
  retrying a timed-out enquiry can double-submit it to the agent. Track your own
  submission state; do not blind-retry writes.
- **Rate limits are two-dimensional**: 1000–3000 requests/minute (by plan, even
  on Unlimited) *and* a per-package daily quota that resets at 10am AEST. Watch
  `X-Quota-PerMinute-Remaining` and `X-Quota-PerDay-Remaining` and slow down
  before you hit 429.
- **Attribution.** Listing data must be displayed under Domain's Attribution and
  Usage Policies.
- Full conventions: `conventions/domain-group-conventions.yml`.
