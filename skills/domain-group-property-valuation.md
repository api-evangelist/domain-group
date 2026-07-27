---
name: Value an Australian property with Domain
description: >-
  Resolve a free-text Australian address to a Domain property id, then pull the
  sale price estimate, the rental estimate, and the supporting sales and listing
  history for that property.
api: openapi/domain-group-openapi-latest.json
operations:
  - Properties_Suggest
  - AddressLocators_Get
  - Properties_Get
  - Properties_GetPriceEstimate
  - Properties_GetRentalEstimate
  - property_sales_history_get
  - property_listing_history_get
  - PropertyAvm_Get
  - PropertyAvm_ReportGet
scopes:
  - api_properties_read
  - api_addresslocators_read
  - api_avm_read
generated: '2026-07-26'
method: generated
source: openapi/domain-group-openapi-latest.json + https://developer.domain.com.au/docs/latest
---

# Value an Australian property with Domain

Domain identifies every property with its own opaque property id. Nothing in the
valuation surface accepts a raw address, so the first move is always address →
property id.

## Before you start

- Base URL: `https://api.domain.com.au/` (sandbox: `https://api.domain.com.au/sandbox/`).
- Auth: either the `x-api-key` header, or an OAuth 2.0 bearer token from
  `https://auth.domain.com.au/v1/connect/token`. Client Credentials is enough —
  none of these operations need user context.
- Required scopes: `api_properties_read`, `api_addresslocators_read`,
  `api_avm_read`. Price Estimation, Rental AVM and Property Enrichment are
  **separate API packages** that must be added to your portal project and
  negotiated with an account manager; the two packages granted on signup
  (Agents & Listings, Properties & Locations) do not include them.
- Cache the access token until its expiry — token requests are capped at
  3000/hour and the SLA guarantee is conditional on doing this.

## Steps

1. **Resolve the address.** Call `Properties_Suggest`
   (`GET /v1/properties/_suggest`) with the free-text address. It returns
   candidate properties with their Domain ids. For a stricter address-component
   match use `AddressLocators_Get` (`GET /v1/addressLocators`) instead.
   If several candidates come back, disambiguate on the returned address fields
   before continuing — never guess.

2. **Confirm the property.** Call `Properties_Get`
   (`GET /v1/properties/{id}`) with the chosen id and check the returned address
   matches what the user asked for.

3. **Sale price estimate.** Call `Properties_GetPriceEstimate`
   (`GET /v1/properties/{propertyId}/priceEstimate`). The response carries a
   lower / mid / upper price band, a confidence indicator, and estimate history.
   **Always report the band and the confidence together** — a mid-point quoted
   alone misrepresents the model.

4. **Rental estimate.** Call `Properties_GetRentalEstimate`
   (`GET /v1/properties/{propertyId}/rentalEstimate`) for the rental AVM.

5. **Full AVM (if licensed).** `PropertyAvm_Get` (`GET /v1/avm/{propertyId}`)
   and `PropertyAvm_ReportGet` (`GET /v1/avmReport/{propertyId}`) return the
   richer automated valuation and its report form.

6. **Ground the number in history.** `property_sales_history_get`
   (`GET /v1/properties/salesHistory`) and `property_listing_history_get`
   (`GET /v1/properties/listingHistory`) give the prior transactions and
   campaigns for the property. An estimate with no history behind it is a weak
   answer.

## Rules

- **Attribution is mandatory.** Domain data is licensed under the Domain Group
  API Terms and Conditions and the Attribution and Usage Policies. Do not
  present an estimate as your own valuation.
- **These are model outputs, not appraisals.** Carry Domain's confidence
  indicator through to the user; never round it away.
- **403 with `X-Domain-Security-Reason`** almost always means the package is not
  on your project plan or the token is missing `api_avm_read` /
  `api_properties_read`. Read that header before retrying anything.
- **429**: honour `Retry-After` (seconds) and check `X-Quota-Exceeded` to see
  whether you hit the per-minute or per-day limit. Daily quotas reset at 10am AEST.
- See `conventions/domain-group-conventions.yml` and
  `errors/domain-group-problem-types.yml` for the full envelope.
