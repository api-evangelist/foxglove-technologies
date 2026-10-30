# Foxglove Technologies

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

Foxglove Technologies, Inc. (foxglove.dev) builds a multimodal data platform for robotics, autonomy and physical AI. Its products cover visualization and debugging of robot data (3D scenes, images, plots, logs, maps), cloud and self-hosted data infrastructure for recording ingest and retention, fleet and device management, and an agent layer that lets AI assistants inspect recordings. Foxglove publishes an OpenAPI 3.1 REST API at api.foxglove.dev/v1 for devices, recordings, sessions, events, event types, custom properties, sites, tokens, extensions and layouts; a webhook event surface; SDKs for Python, Rust, C++, C, Go and TypeScript; a Go CLI; and the open-source MCAP container format and Foxglove message schemas.

**Areas:** Robotics · Observability · Visualization · Data Platform · Physical AI · Autonomy · Fleet Management · Developer Tools · MCAP · ROS

## Foxglove Technologies on APIs.io

Everything profiled for Foxglove Technologies is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/foxglove-technologies/](https://apis.io/providers/foxglove-technologies/)** — or go straight to one of the APIs or properties below.

### APIs (20)

- [Foxglove Technologies Coverage API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-coverage-api/) — Coverage provides the ability to see which time spans are available within Foxglove.
- [Foxglove Technologies Custom Properties API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-custom-properties-api/) — Custom properties are typed metadata which you can assign to devices. For example, you can create a device custom property identified with a key…
- [Foxglove Technologies Device Tokens API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-device-tokens-api/) — Device tokens authenticate a device to the API.
- [Foxglove Technologies Devices API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-devices-api/) — Devices represent robots in your organization. It is common to have devices for both physical and virtual robots. Devices are referenced by other resources…
- [Foxglove Technologies Event Types API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-event-types-api/) — Event types help ensure data quality through validation, enable better filtering and analytics, and provide visual distinctions between categories of events.
- [Foxglove Technologies Events API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-events-api/) — Adding events can help you quickly identify, categorize, and search for points of interest in your data. Each event is tied to a device and time span, and…
- [Foxglove Technologies Extensions API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-extensions-api/) — The Extensions API from Foxglove Technologies — 3 operation(s) for extensions.
- [Foxglove Technologies Imports API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-imports-api/) — **The Imports endpoints are deprecated. Use the [Recordings](#tag/Recordings) endpoints instead.** Imports are recordings that are available at a Primary Site.
- [Foxglove Technologies Lake files API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-lake-files-api/) — MCAP files stored in the lake bucket of a [self-hosted Primary Site](https://docs.foxglove.dev/docs/primary-sites#self-hosted). You must have an Enterprise…
- [Foxglove Technologies Layouts API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-layouts-api/) — The Layouts API from Foxglove Technologies — 3 operation(s) for layouts.
- [Foxglove Technologies Projects API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-projects-api/) — [Projects](https://docs.foxglove.dev/docs/projects) are a container for organizing data and resources in Foxglove. Your plan must support managing projects.
- [Foxglove Technologies Properties API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-properties-api/) — The Properties API from Foxglove Technologies — 3 operation(s) for properties.
- [Foxglove Technologies Recording Attachments API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-recording-attachments-api/) — A recording attachment resource represents information about an MCAP attachment imported to Foxglove. Attachments are available for individual download or…
- [Foxglove Technologies Recordings API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-recordings-api/) — A recording is a resource representing the content of an MCAP file or ROS bag managed by Data Platform.
- [Foxglove Technologies Sessions API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-sessions-api/) — Sessions are logical groupings of recordings from a single device. They allow you to manage and interact with recording data independent of how the…
- [Foxglove Technologies Site Inbox Notification Tokens API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-site-inbox-notification-tokens-api/) — Site inbox notification tokens are credentials used to authenticate bucket notifications for a [Primary Site](https://docs.foxglove.dev/docs/primary-sites)…
- [Foxglove Technologies Site Tokens API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-site-tokens-api/) — Site tokens are credentials a [self-hosted Primary Site](https://docs.foxglove.dev/docs/primary-sites#self-hosted) or [Edge…
- [Foxglove Technologies Sites API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-sites-api/) — A site is a logical grouping of storage and compute for storing Recording data.
- [Foxglove Technologies Stream data API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-stream-data-api/) — The Stream data API from Foxglove Technologies — 1 operation(s) for stream data.
- [Foxglove Technologies Topics API](https://apis.io/apis/foxglove-technologies/foxglove-technologies-topics-api/) — Topics provide schema information for messages in the data source.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Foxglove Technologies Webhooks](https://apis.io/asyncapis/foxglove-technologies/foxglove-technologies-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [foxglove](https://apis.io/servers/foxglove-technologies/foxglove/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Foxglove Technologies Agentic Access](https://apis.io/agentic-access/foxglove-technologies/foxglove-technologies-agentic-access/)

#### JSON Schema (50)

The data models the API reads and writes.

- [foxglove.ArrowPrimitive](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-arrowprimitive/)
- [foxglove.CameraCalibration](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-cameracalibration/)
- [foxglove.CircleAnnotation](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-circleannotation/)
- [foxglove.Color](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-color/)
- [foxglove.CompressedAudio](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-compressedaudio/)
- [foxglove.CompressedImage](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-compressedimage/)
- [foxglove.CompressedPointCloud](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-compressedpointcloud/)
- [foxglove.CompressedVideo](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-compressedvideo/)
- [foxglove.CubePrimitive](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-cubeprimitive/)
- [foxglove.CylinderPrimitive](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-cylinderprimitive/)
- [foxglove.Duration](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-duration/)
- [foxglove.Event](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-event/)
- [foxglove.FrameTransform](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-frametransform/)
- [foxglove.FrameTransforms](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-frametransforms/)
- [foxglove.GeoJSON](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-geojson/)
- [foxglove.Grid](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-grid/)
- [foxglove.ImageAnnotations](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-imageannotations/)
- [foxglove.JointState](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-jointstate/)
- [foxglove.JointStates](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-jointstates/)
- [foxglove.KeyValuePair](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-keyvaluepair/)
- [foxglove.LaserScan](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-laserscan/)
- [foxglove.LinePrimitive](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-lineprimitive/)
- [foxglove.LocationFix](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-locationfix/)
- [foxglove.LocationFixes](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-locationfixes/)
- [foxglove.Log](https://apis.io/schemas/foxglove-technologies/foxglove-technologies-log/)
- …and 25 more published on APIs.io

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Foxglove Technologies Api Overlay](https://apis.io/overlays/foxglove-technologies/foxglove-technologies-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Foxglove Technologies Authentication](https://apis.io/security/foxglove-technologies/foxglove-technologies-authentication/)
- [Foxglove Technologies Domain Security](https://apis.io/security/foxglove-technologies/foxglove-technologies-domain-security/)
- [Foxglove Technologies Trust Center](https://apis.io/security/foxglove-technologies/foxglove-technologies-trust-center/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Foxglove Technologies Plans Pricing](https://apis.io/plans/foxglove-technologies/foxglove-technologies-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Foxglove Technologies Rate Limits](https://apis.io/rate-limits/foxglove-technologies/foxglove-technologies-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://foxglove.dev)
- [Documentation](https://docs.foxglove.dev/docs)
- [Getting started](https://docs.foxglove.dev/docs/getting-started-guide)
- [API reference](https://docs.foxglove.dev/api)
- [Pricing](https://foxglove.dev/pricing)
- [Sign up](https://app.foxglove.dev/)
- [Support](https://foxglove.dev/contact)
- [Changelog](https://docs.foxglove.dev/changelog)
- [Blog](https://foxglove.dev/blog)
- [Compliance](https://foxglove.dev/security)
- [Terms of service](https://foxglove.dev/legal/terms)
- [Privacy policy](https://foxglove.dev/legal/privacy)
- [GitHub](https://github.com/foxglove)
- [Status](https://status.foxglove.dev/)

## API Evangelist rating

**Kin Score 59.4** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 55.9 |
| Contract governance | 4.5 |
| Operational transparency | 34.2 |
| Developer ergonomics | 80.4 |
| Access clarity | 78.9 |

**Agent readiness 37.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 29.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/foxglove-technologies/](https://apis.io/providers/foxglove-technologies/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Foxglove Technologies: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/foxglove-technologies/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
