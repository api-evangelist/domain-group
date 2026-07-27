---
name: Pull Australian suburb market data from Domain
description: >-
  Assemble a suburb market picture - performance statistics, historical series,
  demographics, weekend auction and sales results, and nearby schools - the way
  banks and fintechs consume Domain.
api: openapi/domain-group-openapi-latest.json
operations:
  - SuburbPerformance_Get_ByNamedSuburb
  - SuburbPerformance_Get_ByNamedSuburb_WithoutPostcode
  - SuburbHistorical_Get
  - SuburbSummary_Get
  - Demographics_Get_ByNamedSuburb
  - LocationProfiles_Get
  - SalesResults_Get
  - SalesResults_Listings
  - SalesResults_SaturdayReport
  - SalesResults_WeeklyMediaReport
  - Schools_Search_ByLocation
  - Schools_Get_ById
scopes:
  - api_suburbperformance_read
  - api_demographics_read
  - api_locations_read
  - api_salesresults_read
  - api_schools_read
generated: '2026-07-26'
method: generated
source: openapi/domain-group-openapi-latest.json + https://developer.domain.com.au/docs/latest/apis/pkg_properties_locations
---

# Pull Australian suburb market data from Domain

This is the package banks and fintechs actually buy Domain for: suburb medians,
market performance and demographics, rather than individual listings.

## Before you start

- Suburb-keyed endpoints take an **(state, suburb, postcode)** triple —
  e.g. `NSW / Pyrmont / 2009`. State is the Australian abbreviation
  (NSW, VIC, QLD, WA, SA, TAS, ACT, NT).
- Scopes vary by endpoint family: `api_suburbperformance_read`,
  `api_demographics_read`, `api_locations_read`, `api_salesresults_read`,
  `api_schools_read`. Schools is a separately-negotiated package.
- Client Credentials is sufficient throughout — no user context needed.

## Steps

1. **Performance statistics.** `SuburbPerformance_Get_ByNamedSuburb`
   (`GET /v2/suburbPerformanceStatistics/{state}/{suburb}/{postcode}`) is the
   headline series — medians, days on market, discounting, auction clearance.
   If you do not have the postcode, use
   `SuburbPerformance_Get_ByNamedSuburb_WithoutPostcode`
   (`GET /v2/suburbPerformanceStatistics/{state}/{suburb}`) — but be aware that
   suburb names repeat across Australian states and even within one, so supply
   the postcode whenever you have it.

   > Note: the v1 equivalent `SuburbPerformanceStatistics_Get` is flagged
   > `deprecated: true` in the v1 OpenAPI document. Build on the v2 operation.

2. **Historical series.** `SuburbHistorical_Get`
   (`GET /v1/suburbHistorical/{state}/{suburb}/{postcode}`) for the longer run,
   and `SuburbSummary_Get` (`GET /v1/suburbSummary/{state}/{suburb}/{postcode}`)
   for the condensed view.

3. **Demographics.** `Demographics_Get_ByNamedSuburb`
   (`GET /v2/demographics/{state}/{suburb}/{postcode}`).

4. **Location profile.** `LocationProfiles_Get`
   (`GET /v1/locations/profiles/{domainLocationId}`) — resolve the Domain
   location id first via `ListingLocations_Search` (`GET /v1/listings/locations`).

5. **Auction and sales results.** `SalesResults_Get`
   (`GET /v1/salesResults/{city}`) for the capital-city weekend result,
   `SalesResults_Listings` (`GET /v1/salesResults/{city}/listings`) for the
   underlying listings, and the v2 reports
   `SalesResults_SaturdayReport` (`GET /v2/salesResults/saturday`) and
   `SalesResults_WeeklyMediaReport` (`GET /v2/salesResults/weeklyMedia`).

6. **Schools.** `Schools_Search_ByLocation`
   (`GET /v2/schools/{latitude}/{longitude}`) for catchment-style context, and
   `Schools_Get_ById` (`GET /v2/schools/{id}`) for the detail.

## Rules

- **Australia only.** Domain has no coverage outside Australia and uses no RESO /
  MLS identifiers; properties carry opaque Domain ids and, in PropertyRadar, the
  Australian G-NAF address id.
- **Batch inside your quota.** A suburb sweep is quota-hungry: each package
  carries its own daily quota that resets at 10am AEST, on top of the
  1000–3000 req/min ceiling. Read `X-Quota-PerDay-Remaining` on every response
  and schedule accordingly.
- **Cache aggressively.** These series update weekly at most; re-pulling them
  per user request wastes quota and adds nothing.
- **Attribution is mandatory** under the Domain Group API Terms and Conditions.
