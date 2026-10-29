# Domain Group

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Domain Group (Domain Holdings Australia Ltd, trading as domain.com.au) is the second of Australia's two national residential property portals, alongside REA Group's realestate.com.au, and since 27 August 2025 has been a wholly owned subsidiary of CoStar Group. Headquartered in Sydney, Domain operates the domain.com.au consumer marketplace plus commercial, agent, and developer-project brands, and sits in the middle of the Australian value chain between selling and leasing agencies on one side and buyers, renters, banks, and PropTech builders on the other. Unlike most of the real estate sector, Domain runs a genuine, self-serve public developer portal at developer.domain.com.au: a developer signs up with GitHub, Google, or email, creates a project, and is immediately granted the "Agents & Listings" and "Properties & Locations" packages, with the remaining eleven packages - Address Suggestions, Campaign reporting, Listings Management, Price Estimation, Property Enrichment, Property Package, PropertyRadar, Rental AVM, Schools Data, and Webhooks - added per project and negotiated with an account manager. Domain publishes three machine-readable OpenAPI 3.0.4 documents (latest, v1, v2) directly from its Libraries page, backs them with an OpenID Connect discovery document at auth.domain.com.au, and serves everything from api.domain.com.au behind API-key or OAuth 2.0 (client credentials, authorization code, implicit) credentials. Write access is a different gate entirely: uploading or updating listings requires sandbox sign-off by email to api@domain.com.au and written permission from the principal agent of each agency, making listing management broker-authorised even though the read surface is self-serve. Domain carries no RESO Web API or RESO Data Dictionary certification, exposes no OData $metadata document and no Universal Property Identifier - RESO is a North American NAR-driven standard with no presence in the Australian portal duopoly - and it publishes no open, unlicensed dataset; all data is licensed under the Domain Group API Terms and Conditions.

**Areas:** Real Estate · Australia · Property Listings · Property Data · Valuation · AVM · Rentals · Listing Management · PropTech · Portal Marketplace

## Domain Group on APIs.io

Everything profiled for Domain Group is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/domain-group/](https://apis.io/providers/domain-group/)** — or go straight to one of the APIs or properties below.

### APIs (31)

- [Domain Group Address Locators API](https://apis.io/apis/domain-group/domain-group-addresslocators-api/) — The AddressLocators API from Domain Group — 1 operation(s) for addresslocators.
- [Domain Group Agencies API](https://apis.io/apis/domain-group/domain-group-agencies-api/) — The Agencies API from Domain Group — 6 operation(s) for agencies.
- [Domain Group Agents API](https://apis.io/apis/domain-group/domain-group-agents-api/) — The Agents API from Domain Group — 5 operation(s) for agents.
- [Domain Group Authorities API](https://apis.io/apis/domain-group/domain-group-authorities-api/) — The Authorities API from Domain Group — 6 operation(s) for authorities.
- [Domain Group Campaign Reporting API](https://apis.io/apis/domain-group/domain-group-campaignreporting-api/) — The CampaignReporting API from Domain Group — 3 operation(s) for campaignreporting.
- [Domain Group Dataset API](https://apis.io/apis/domain-group/domain-group-dataset-api/) — The Dataset API from Domain Group — 1 operation(s) for dataset.
- [Domain Group Demographics API](https://apis.io/apis/domain-group/domain-group-demographics-api/) — The Demographics API from Domain Group — 1 operation(s) for demographics.
- [Domain Group Disclaimers API](https://apis.io/apis/domain-group/domain-group-disclaimers-api/) — The Disclaimers API from Domain Group — 2 operation(s) for disclaimers.
- [Domain Group Enquiries API](https://apis.io/apis/domain-group/domain-group-enquiries-api/) — The Enquiries API from Domain Group — 2 operation(s) for enquiries.
- [Domain Group Leadscope API](https://apis.io/apis/domain-group/domain-group-leadscope-api/) — The Leadscope API from Domain Group — 2 operation(s) for leadscope.
- [Domain Group Listings API](https://apis.io/apis/domain-group/domain-group-listings-api/) — The Listings API from Domain Group — 19 operation(s) for listings.
- [Domain Group Listing Search API](https://apis.io/apis/domain-group/domain-group-listingsearch-api/) — The ListingSearch API from Domain Group — 2 operation(s) for listingsearch.
- [Domain Group Locations API](https://apis.io/apis/domain-group/domain-group-locations-api/) — The Locations API from Domain Group — 1 operation(s) for locations.
- [Domain Group Me API](https://apis.io/apis/domain-group/domain-group-me-api/) — The Me API from Domain Group — 3 operation(s) for me.
- [Domain Group Pre Market API](https://apis.io/apis/domain-group/domain-group-premarket-api/) — The PreMarket API from Domain Group — 2 operation(s) for premarket.
- [Domain Group Products API](https://apis.io/apis/domain-group/domain-group-products-api/) — The Products API from Domain Group — 8 operation(s) for products.
- [Domain Group Projects API](https://apis.io/apis/domain-group/domain-group-projects-api/) — The Projects API from Domain Group — 6 operation(s) for projects.
- [Domain Group Properties API](https://apis.io/apis/domain-group/domain-group-properties-api/) — The Properties API from Domain Group — 10 operation(s) for properties.
- [Domain Group Property Avm API](https://apis.io/apis/domain-group/domain-group-propertyavm-api/) — The PropertyAvm API from Domain Group — 2 operation(s) for propertyavm.
- [Domain Group Property Features API](https://apis.io/apis/domain-group/domain-group-propertyfeatures-api/) — The PropertyFeatures API from Domain Group — 1 operation(s) for propertyfeatures.
- [Domain Group Property Like API](https://apis.io/apis/domain-group/domain-group-propertylike-api/) — The PropertyLike API from Domain Group — 1 operation(s) for propertylike.
- [Domain Group Property Radar API](https://apis.io/apis/domain-group/domain-group-propertyradar-api/) — The PropertyRadar API from Domain Group — 7 operation(s) for propertyradar.
- [Domain Group Property Zoning Perils API](https://apis.io/apis/domain-group/domain-group-propertyzoningperils-api/) — The PropertyZoningPerils API from Domain Group — 1 operation(s) for propertyzoningperils.
- [Domain Group Sales Results API](https://apis.io/apis/domain-group/domain-group-salesresults-api/) — The SalesResults API from Domain Group — 5 operation(s) for salesresults.
- [Domain Group Schools API](https://apis.io/apis/domain-group/domain-group-schools-api/) — The Schools API from Domain Group — 2 operation(s) for schools.
- [Domain Group Statistics API](https://apis.io/apis/domain-group/domain-group-statistics-api/) — The Statistics API from Domain Group — 6 operation(s) for statistics.
- [Domain Group Webhooks API](https://apis.io/apis/domain-group/domain-group-webhooks-api/) — The Webhooks API from Domain Group — 2 operation(s) for webhooks.
- [Domain Group Avm History API](https://apis.io/apis/domain-group/domain-group-avmhistory-api/) — The Avm History API from Domain Group — 1 operation(s) for property valuation history (GET /v1/avmHistory/{propertyId}, "Retrieves valuation history for the…
- [Domain Group Auction Collection API](https://apis.io/apis/domain-group/domain-group-auctioncollection-api/) — The Auction Collection API from Domain Group — 2 operation(s) for auction collection: the auction calling sheet of auctions without results yet (GET…
- [Domain Group Agent Search API](https://apis.io/apis/domain-group/domain-group-agentsearch-api/) — The Agent Search API from Domain Group — 1 operation(s) for agent search by location (POST /v2/agentsearch/agents/location, "Retrieves agents matching the…
- [Domain Group Property Search API](https://apis.io/apis/domain-group/domain-group-property-search-api/) — The Property Search API from Domain Group — 1 operation(s) for property search.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (2)

Event-driven and webhook contracts.

- [Domain Group Webhooks](https://apis.io/asyncapis/domain-group/domain-group-webhooks/)
- [Domain Group Webhooks](https://apis.io/asyncapis/domain-group/domain-group-webhooks-asyncapi/)

#### Event channels (7)

Individual events and webhooks the provider emits.

- [agencies](https://apis.io/channels/domain-group/agencies/)
- [agents](https://apis.io/channels/domain-group/agents/)
- [enquiries](https://apis.io/channels/domain-group/enquiries/)
- [heartbeat](https://apis.io/channels/domain-group/heartbeat/)
- [listingProcessingReports](https://apis.io/channels/domain-group/listingprocessingreports/)
- [listings](https://apis.io/channels/domain-group/listings/)
- [projects](https://apis.io/channels/domain-group/projects/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [domain-group](https://apis.io/servers/domain-group/domain-group/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Domain Group Agentic Access](https://apis.io/agentic-access/domain-group/domain-group-agentic-access/)

#### JSON Schema (76)

The data models the API reads and writes.

- [Agencies.V1.Agent](https://apis.io/schemas/domain-group/domain-group-agencies-v1-agent/)
- [Agencies.V2.Agency](https://apis.io/schemas/domain-group/domain-group-agencies-v2-agency/)
- [Agencies.V2.AgencySummary](https://apis.io/schemas/domain-group/domain-group-agencies-v2-agency-summary/)
- [Agencies.V2.AgentReviewLiteResponse](https://apis.io/schemas/domain-group/domain-group-agencies-v2-agent-review-lite-response/)
- [Agencies.V2.AgentSearchPageResultContactStatsDto](https://apis.io/schemas/domain-group/domain-group-agencies-v2-agent-search-page-result-contact-stats-dto/)
- [Agencies.V2.GetAgentsByLocationRequest](https://apis.io/schemas/domain-group/domain-group-agencies-v2-get-agents-by-location-request/)
- [AuctionCollection.v1.CallingSheetResponse](https://apis.io/schemas/domain-group/domain-group-auction-collection-v1-calling-sheet-response/)
- [AuctionCollection.v1.PutAuctionUpdateRequest](https://apis.io/schemas/domain-group/domain-group-auction-collection-v1-put-auction-update-request/)
- [AuctionResults.v1.listingEventItem](https://apis.io/schemas/domain-group/domain-group-auction-results-v1-listing-event-item/)
- [AuctionResults.v1.summaryResponse](https://apis.io/schemas/domain-group/domain-group-auction-results-v1-summary-response/)
- [Authorities.v1.Attachments](https://apis.io/schemas/domain-group/domain-group-authorities-v1-attachments/)
- [Authorities.v1.AuthorityRequest](https://apis.io/schemas/domain-group/domain-group-authorities-v1-authority-request/)
- [Authorities.v1.AuthorityResponse](https://apis.io/schemas/domain-group/domain-group-authorities-v1-authority-response/)
- [Authorities.v1.SubscriptionRequest](https://apis.io/schemas/domain-group/domain-group-authorities-v1-subscription-request/)
- [Authorities.v1.SubscriptionResponse](https://apis.io/schemas/domain-group/domain-group-authorities-v1-subscription-response/)
- [Authorities.v1.VendorAttachments](https://apis.io/schemas/domain-group/domain-group-authorities-v1-vendor-attachments/)
- [AvmHistory.v1.Response](https://apis.io/schemas/domain-group/domain-group-avm-history-v1-response/)
- [BookingV2Api.v1.GetListingPriceQuoteByAgencyResponse](https://apis.io/schemas/domain-group/domain-group-booking-v2-api-v1-get-listing-price-quote-by-agency-response/)
- [BookingV2Api.v1.GetQuoteListingPriceBySuburbsRequest](https://apis.io/schemas/domain-group/domain-group-booking-v2-api-v1-get-quote-listing-price-by-suburbs-request/)
- [BookingV2Api.v1.GetQuoteListingPriceBySuburbsResponse](https://apis.io/schemas/domain-group/domain-group-booking-v2-api-v1-get-quote-listing-price-by-suburbs-response/)
- [Bookings.V2.RateForNewListing](https://apis.io/schemas/domain-group/domain-group-bookings-v2-rate-for-new-listing/)
- [Bookings.V2.RateForNewListingRequest](https://apis.io/schemas/domain-group/domain-group-bookings-v2-rate-for-new-listing-request/)
- [CampaignAPI.v1.ListingPerformanceDataResponse](https://apis.io/schemas/domain-group/domain-group-campaign-api-v1-listing-performance-data-response/)
- [CampaignAPI.v1.ProjectPerformanceDataResponse](https://apis.io/schemas/domain-group/domain-group-campaign-api-v1-project-performance-data-response/)
- [CampaignAPI.v1.SocialPerformanceDataResponse](https://apis.io/schemas/domain-group/domain-group-campaign-api-v1-social-performance-data-response/)
- …and 51 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Domain Group Context](https://apis.io/jsonld/domain-group/domain-group-context/)

#### Collections (3)

Postman and Open Collection request collections.

- [Domain Public API](https://apis.io/collections/domain-group/open-domain-group-openapi-latest/)
- [Domain Public API](https://apis.io/collections/domain-group/open-domain-group-openapi-v1/)
- [Domain Public API](https://apis.io/collections/domain-group/open-domain-group-openapi-v2/)

#### Overlays (31)

OpenAPI overlays, including conversational phrasing for each operation.

- [Domain Group Addresslocators Api Overlay](https://apis.io/overlays/domain-group/domain-group-addresslocators-api-overlay/)
- [Domain Group Agencies Api Overlay](https://apis.io/overlays/domain-group/domain-group-agencies-api-overlay/)
- [Domain Group Agents Api Overlay](https://apis.io/overlays/domain-group/domain-group-agents-api-overlay/)
- [Domain Group Agentsearch Api Overlay](https://apis.io/overlays/domain-group/domain-group-agentsearch-api-overlay/)
- [Domain Group Auctioncollection Api Overlay](https://apis.io/overlays/domain-group/domain-group-auctioncollection-api-overlay/)
- [Domain Group Authorities Api Overlay](https://apis.io/overlays/domain-group/domain-group-authorities-api-overlay/)
- [Domain Group Avmhistory Api Overlay](https://apis.io/overlays/domain-group/domain-group-avmhistory-api-overlay/)
- [Domain Group Campaignreporting Api Overlay](https://apis.io/overlays/domain-group/domain-group-campaignreporting-api-overlay/)
- [Domain Group Dataset Api Overlay](https://apis.io/overlays/domain-group/domain-group-dataset-api-overlay/)
- [Domain Group Demographics Api Overlay](https://apis.io/overlays/domain-group/domain-group-demographics-api-overlay/)
- [Domain Group Disclaimers Api Overlay](https://apis.io/overlays/domain-group/domain-group-disclaimers-api-overlay/)
- [Domain Group Enquiries Api Overlay](https://apis.io/overlays/domain-group/domain-group-enquiries-api-overlay/)
- [Domain Group Leadscope Api Overlay](https://apis.io/overlays/domain-group/domain-group-leadscope-api-overlay/)
- [Domain Group Listings Api Overlay](https://apis.io/overlays/domain-group/domain-group-listings-api-overlay/)
- [Domain Group Listingsearch Api Overlay](https://apis.io/overlays/domain-group/domain-group-listingsearch-api-overlay/)
- [Domain Group Locations Api Overlay](https://apis.io/overlays/domain-group/domain-group-locations-api-overlay/)
- [Domain Group Me Api Overlay](https://apis.io/overlays/domain-group/domain-group-me-api-overlay/)
- [Domain Group Premarket Api Overlay](https://apis.io/overlays/domain-group/domain-group-premarket-api-overlay/)
- [Domain Group Products Api Overlay](https://apis.io/overlays/domain-group/domain-group-products-api-overlay/)
- [Domain Group Projects Api Overlay](https://apis.io/overlays/domain-group/domain-group-projects-api-overlay/)
- [Domain Group Properties Api Overlay](https://apis.io/overlays/domain-group/domain-group-properties-api-overlay/)
- [Domain Group Property Search Api Overlay](https://apis.io/overlays/domain-group/domain-group-property-search-api-overlay/)
- [Domain Group Propertyavm Api Overlay](https://apis.io/overlays/domain-group/domain-group-propertyavm-api-overlay/)
- [Domain Group Propertyfeatures Api Overlay](https://apis.io/overlays/domain-group/domain-group-propertyfeatures-api-overlay/)
- [Domain Group Propertylike Api Overlay](https://apis.io/overlays/domain-group/domain-group-propertylike-api-overlay/)
- …and 6 more published on APIs.io

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Domain Group API Rules](https://apis.io/rules/domain-group/domain-group-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Domain Group Authentication](https://apis.io/security/domain-group/domain-group-authentication/)
- [Domain Group Domain Security](https://apis.io/security/domain-group/domain-group-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Domain Group Scopes](https://apis.io/scopes/domain-group/domain-group-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Domain Group Plans Pricing](https://apis.io/plans/domain-group/domain-group-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Domain Group Rate Limits](https://apis.io/rate-limits/domain-group/domain-group-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.domain.com.au/)
- [Documentation](https://developer.domain.com.au/docs/latest)
- [Getting started](https://developer.domain.com.au/docs/latest/getting-started)
- [API reference](https://developer.domain.com.au/docs/latest/apis)
- [Sign up](https://developer.domain.com.au/docs/latest/getting-started/creating-first-project)
- [Support](https://developer.domain.com.au/docs/latest/support)
- [Terms of service](https://www.domain.com.au/group/api-terms-and-conditions/)
- [GitHub](https://github.com/domain-group)

## API Evangelist rating

**Kin Score 58.7** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 69.7 |
| Contract governance | 22.0 |
| Operational transparency | 65.8 |
| Developer ergonomics | 63.7 |
| Access clarity | 23.7 |

**Agent readiness 43.6** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | mostly |

**Regulatory alignment 30.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/domain-group/](https://apis.io/providers/domain-group/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Domain Group: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/domain-group/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
