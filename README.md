# Domain Group (domain-group)

Domain Group (Domain Holdings Australia Ltd, trading as domain.com.au) is the second of Australia's two national residential property portals, alongside REA Group's realestate.com.au, and since 27 August 2025 has been a wholly owned subsidiary of CoStar Group. Headquartered in Sydney, Domain operates the domain.com.au consumer marketplace plus commercial, agent, and developer-project brands, and sits in the middle of the Australian value chain between selling and leasing agencies on one side and buyers, renters, banks, and PropTech builders on the other. Unlike most of the real estate sector, Domain runs a genuine, self-serve public developer portal at developer.domain.com.au: a developer signs up with GitHub, Google, or email, creates a project, and is immediately granted the "Agents & Listings" and "Properties & Locations" packages, with the remaining eleven packages - Address Suggestions, Campaign reporting, Listings Management, Price Estimation, Property Enrichment, Property Package, PropertyRadar, Rental AVM, Schools Data, and Webhooks - added per project and negotiated with an account manager. Domain publishes three machine-readable OpenAPI 3.0.4 documents (latest, v1, v2) directly from its Libraries page, backs them with an OpenID Connect discovery document at auth.domain.com.au, and serves everything from api.domain.com.au behind API-key or OAuth 2.0 (client credentials, authorization code, implicit) credentials. Write access is a different gate entirely: uploading or updating listings requires sandbox sign-off by email to api@domain.com.au and written permission from the principal agent of each agency, making listing management broker-authorised even though the read surface is self-serve. Domain carries no RESO Web API or RESO Data Dictionary certification, exposes no OData $metadata document and no Universal Property Identifier - RESO is a North American NAR-driven standard with no presence in the Australian portal duopoly - and it publishes no open, unlicensed dataset; all data is licensed under the Domain Group API Terms and Conditions.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/domain-group/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/domain-group/refs/heads/main/apis.yml)

## Tags

- Real Estate
- Australia
- Property Listings
- Property Data
- Valuation
- AVM
- Rentals
- Listing Management
- PropTech
- Portal Marketplace

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

### Domain Address Suggestions API

Search for valid Australian property addresses and resolve them to Domain property identifiers. Backed by GET /v1/properties/_suggest and GET /v1/addressLocators. Requires the api_properties_read or api_addresslocators_read scope.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_address_suggestion](https://developer.domain.com.au/docs/latest/apis/pkg_address_suggestion)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Address
- Geocoding
- Real Estate

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_address_suggestion)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_address_suggestion/references/properties_suggest)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Agents & Listings API

Access data on agencies, agents, and for-sale, for-rent, commercial, business, and project listings directly from Domain. Covers agency and agent search and profiles, residential/commercial/business listing search, listing locations, project search, and enquiry submission. Granted automatically on signup along with Properties & Locations.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_agents_listings](https://developer.domain.com.au/docs/latest/apis/pkg_agents_listings)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Property Listings
- Agents
- Agencies
- Real Estate

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [OpenAPI](openapi/domain-group-openapi-v1.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_agents_listings)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_agents_listings/references/listings_detailedresidentialsearch)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Campaign API

Lets authenticated media agencies retrieve advertising campaign performance metrics for Domain listings and developer projects, via GET /v1/campaign/listing-performance and GET /v1/campaign/project-performance. Restricted to authorised media agency clients.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_campaign_api](https://developer.domain.com.au/docs/latest/apis/pkg_campaign_api)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Advertising
- Analytics
- Real Estate

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_campaign_api)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_campaign_api/references/campaign_getlistingperformance_report)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Campaign API - Preview

Preview channel of the Campaign API, giving authorised media agencies early access to campaign performance metrics ahead of general release. Documented as a separate API package on the Domain developer portal.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_campaign_api_preview](https://developer.domain.com.au/docs/latest/apis/pkg_campaign_api_preview)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Advertising
- Analytics
- Preview

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_campaign_api_preview)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Listings Management API

View, create, and update residential, commercial, business, project, and off-market listings on domain.com.au, and manage the resulting enquiries, listing reports, and performance statistics. This is the CRM upload surface used by Australian agency software; production access requires a sandbox sign-off process by email to api@domain.com.au plus written authorisation from the principal agent of each agency whose listings are being managed.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_listing_management](https://developer.domain.com.au/docs/latest/apis/pkg_listing_management)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Listing Management
- CRM
- Enquiries
- Real Estate

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [OpenAPI](openapi/domain-group-openapi-v2.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_listing_management)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_listing_management/guides/upload-listings)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_listing_management/guides/agency-authorisation)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_listing_management/guides/production-access)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_listing_management/guides/migrating-from-xml)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Price Estimation API

Returns the current automated price estimate for a Domain property identifier via GET /v1/properties/{propertyId}/priceEstimate, including lower, mid, and upper price, a confidence indicator, and estimate history. Requires the api_properties_read scope.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_price_estimation](https://developer.domain.com.au/docs/latest/apis/pkg_price_estimation)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Valuation
- AVM
- Property Data

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_price_estimation)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_price_estimation/references/properties_getpriceestimate)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Properties & Locations API

Property records, address locators, location profiles, weekend auction and sales results, suburb performance and historical statistics, and suburb demographics. Granted automatically on signup along with Agents & Listings, and the package most commonly used by banks and fintechs for suburb medians and market performance.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_properties_locations](https://developer.domain.com.au/docs/latest/apis/pkg_properties_locations)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Property Data
- Market Statistics
- Demographics
- Auction Results

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [OpenAPI](openapi/domain-group-openapi-v2.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_properties_locations)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_properties_locations/references/suburbperformance_get_bynamedsuburb)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Property Enrichment API

Enhances a known property with additional Domain-held detail through GET /v1/propertyenrichment, alongside the v2 property features and zoning/perils endpoints. Sold as a separate API package.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_property_enrichment](https://developer.domain.com.au/docs/latest/apis/pkg_property_enrichment)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Property Data
- Enrichment
- Zoning

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_property_enrichment)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_property_enrichment/references/propertyenrichment_get)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Property Package API

A bundled package giving comprehensive property coverage in one subscription - address suggestion, property records, price estimates, residential listing search, location profiles, project data, schools, suburb performance, and demographics - assembled from endpoints that also appear in the narrower packages.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_property](https://developer.domain.com.au/docs/latest/apis/pkg_property)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Property Data
- Bundle
- Real Estate

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_property)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_property/references/properties_get)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain PropertyRadar API

Create and manage watchlist portfolios of properties and read them back in summary or full form, including lookup by G-NAF address identifier. Covers POST/GET/DELETE on /v1/propertyradar/portfolio and its property members. Requires api_propertyportfolio_read and api_propertyportfolio_write scopes.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_propertyradar](https://developer.domain.com.au/docs/latest/apis/pkg_propertyradar)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Property Portfolio
- Monitoring
- Property Data

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_propertyradar)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_propertyradar/references/propertyradar_listportfolios)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Rental AVM API

Automated rental estimates for a Domain property identifier via GET /v1/properties/{propertyId}/rentalEstimate, plus the /v1/avm and /v1/avmReport endpoints. Requires the api_avm_read scope.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_rental_avm](https://developer.domain.com.au/docs/latest/apis/pkg_rental_avm)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Rentals
- AVM
- Valuation

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_rental_avm)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_rental_avm/references/properties_getrentalestimate)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Schools Data API

Detailed information on Australian schools, retrievable by school identifier (GET /v2/schools/{id}) or by latitude and longitude (GET /v2/schools/{latitude}/{longitude}) for school-catchment style property search experiences.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_schools_data](https://developer.domain.com.au/docs/latest/apis/pkg_schools_data)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Schools
- Location Data
- Property Data

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [OpenAPI](openapi/domain-group-openapi-v2.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_schools_data)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_schools_data/references/schools_search_bylocation)
- [DeveloperPortal](https://developer.domain.com.au/)

### Domain Webhooks API

Subscription management for push notifications when data changes in the Domain system. Create, read, list, and delete webhook subscriptions via /v1/webhooks/{id}/subscriptions and /v1/subscriptions/{id}, with configuration, processing, and troubleshooting guides. Requires the api_webhooks_write scope.

- **Human URL:** [https://developer.domain.com.au/docs/latest/apis/pkg_webhooks](https://developer.domain.com.au/docs/latest/apis/pkg_webhooks)
- **Base URL:** `https://api.domain.com.au`

#### Tags

- Webhooks
- Events
- Real Estate

#### Properties

- [OpenAPI](openapi/domain-group-openapi-latest.json)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_webhooks)
- [Documentation](https://developer.domain.com.au/docs/latest/apis/pkg_webhooks/guides/subscriptions)
- [APIReference](https://developer.domain.com.au/docs/latest/apis/pkg_webhooks/references/webhooks_createsubscription)
- [DeveloperPortal](https://developer.domain.com.au/)

## Common Properties

- [Website](https://www.domain.com.au/)
- [DeveloperPortal](https://developer.domain.com.au/)
- [Documentation](https://developer.domain.com.au/docs/latest)
- [APIReference](https://developer.domain.com.au/docs/latest/apis)
- [SignUp](https://developer.domain.com.au/docs/latest/getting-started/creating-first-project)
- [GettingStarted](https://developer.domain.com.au/docs/latest/getting-started)
- [Authentication](https://developer.domain.com.au/docs/latest/authentication)
- [OpenAPI](https://developer.domain.com.au/static/latest/media/latest/openapi.json)
- [WellKnown](well-known/domain-group-openid-configuration.json)
- [OpenIDConnect](https://auth.domain.com.au/v1/.well-known/openid-configuration)
- [RateLimits](https://developer.domain.com.au/docs/latest/conventions/rate-limiting)
- [Sandbox](https://developer.domain.com.au/docs/latest/conventions/sandbox)
- [Conventions](https://developer.domain.com.au/docs/latest/conventions)
- [Versioning](https://developer.domain.com.au/docs/latest/conventions/versioning)
- [Libraries](https://developer.domain.com.au/docs/latest/libraries)
- [SDKs](https://developer.domain.com.au/docs/latest/libraries)
- [Support](https://developer.domain.com.au/docs/latest/support)
- [SLA](https://developer.domain.com.au/docs/latest/support/sla)
- [TermsOfService](https://www.domain.com.au/group/api-terms-and-conditions/)
- [Policies](https://developer.domain.com.au/docs/latest/support/policies)
- [Troubleshooting](https://developer.domain.com.au/docs/latest/troubleshooting)
- [GitHubOrganization](https://github.com/domain-group)

## Maintainers

- Kin Lane — kin@apievangelist.com
