# Virtuagym (virtuagym)

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

Virtuagym is a Netherlands-based fitness and health club management platform that combines member management, membership and billing administration, class and appointment scheduling, access control / check-ins, and digital coaching (workouts, nutrition, and a branded member app) into one SaaS suite for gyms, studios, personal trainers, and corporate wellness programs.

## Access Model (Read This First)

Virtuagym's **authoritative API reference is access-gated**. To use the Public API you:

1. **Request documentation access** by emailing `api@virtuagym.com` with your GitHub username.
2. **Provision credentials** in the Virtuagym portal under **System settings > Business info > Advanced** — this is where your `api_key` and `club_secret` live.
3. **Call the v1 API** at base `https://api.virtuagym.com/api`, passing `api_key` and `club_secret` as **query-string parameters** on every request, over **HTTPS only** (insecure connections are rejected).

Because the official reference is gated, the endpoints, methods, and query parameters in this entry are **grounded in Virtuagym's publicly mirrored API wiki** (`github.com/anokabb/virtuagym-public-api`) and **confirmed against live host probes**. Request/response **bodies are modeled honestly** with additive (`additionalProperties`) schemas and should be reconciled against the official reference once access is granted. Endpoint **paths and methods are confirmed**; full field-level schemas are **modeled**.

- **Base URL:** `https://api.virtuagym.com/api`
- **Auth:** `api_key` + `club_secret` (both required, query parameters) for v1. Legacy v0 used HTTP Basic Auth (deprecated). A separate OAuth 2.0 flow exists for end-user-context calls.
- **Rate limit:** approximately **500 requests/hour** per account; throttling returns status **421**.
- **Change tracking:** poll list endpoints with a `sync_from` millisecond timestamp and a `from_id` cursor. There is **no WebSocket / streaming API** — see `review.yml`.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/virtuagym/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/virtuagym/refs/heads/main/apis.yml)

## Tags

- Fitness
- Health Club Management
- Gym Management
- Coaching
- Membership Management
- Fitness Software
- Wellness
- Scheduling
- SaaS

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

All APIs are club-scoped under `https://api.virtuagym.com/api/v1/club/{club_id}/...` and authenticate with `api_key` + `club_secret`.

### Virtuagym Club Members API

List members edited since a sync point, retrieve a member by internal ID, create members, update members, create-or-update by `external_id`, and activate or connect a member's Virtuagym user profile. Supports lookup by email, `external_id`, RFID tag, and club member ID.

- **Human URL:** [https://support.virtuagym.com/s/article/API-Link-To-Your-Website](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- **Base URL:** `https://api.virtuagym.com/api`

### Virtuagym Club Employees API

List club employees edited since a sync point, retrieve a specific employee, create a new employee, and update an existing one — the staff directory behind a club's coaching, front-desk, and administration workflows.

- **Human URL:** [https://support.virtuagym.com/s/article/API-Link-To-Your-Website](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- **Base URL:** `https://api.virtuagym.com/api`

### Virtuagym Memberships API

Read membership definitions (the plans / products a club sells) and membership instances (a member's enrollment in a plan), with incremental sync via `sync_from` and cursor paging via `from_id`.

- **Human URL:** [https://support.virtuagym.com/s/article/API-Link-To-Your-Website](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- **Base URL:** `https://api.virtuagym.com/api`

### Virtuagym Billing API

Read and assign member credits (class / session balances) and create and retrieve club invoices — the financial surface that pairs membership administration with billing records.

- **Human URL:** [https://support.virtuagym.com/s/article/API-Link-To-Your-Website](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- **Base URL:** `https://api.virtuagym.com/api`

### Virtuagym Visits API

List visits (member check-ins) based on supplied queries such as new visits since `sync_from`, retrieve a single visit, and create a visit — the attendance and access-control record for a club, commonly fed from turnstiles and front-desk check-in.

- **Human URL:** [https://support.virtuagym.com/s/article/API-Link-To-Your-Website](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- **Base URL:** `https://api.virtuagym.com/api`

### Virtuagym Events API

List club events (scheduled classes / sessions) filtered by schedule, member, and a start/end timestamp window, retrieve a single event, and manage event participants — list, add (book), update, retrieve, and remove (cancel) a member's booking.

- **Human URL:** [https://support.virtuagym.com/s/article/API-Link-To-Your-Website](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- **Base URL:** `https://api.virtuagym.com/api`

### Virtuagym Coaching Workouts API

Assign a coaching workout / training plan to a club member, specifying the plan, the member, and scheduling details (weekdays, weeks, and start date) — the digital-coaching surface that pushes structured training into a member's Virtuagym app.

- **Human URL:** [https://support.virtuagym.com/s/article/API-Link-To-Your-Website](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- **Base URL:** `https://api.virtuagym.com/api`

## Common Properties

- [Domain Security](security/virtuagym-domain-security.yml)
- [Authentication](authentication/virtuagym-authentication.yml)
- [GitHub Organization](https://github.com/virtuagym)
- [LinkedIn](https://www.linkedin.com/company/virtuagym)
- [Website](https://virtuagym.com)
- [Documentation](https://support.virtuagym.com/s/article/API-Link-To-Your-Website)
- [Plans](plans/virtuagym-plans-pricing.yml)
- [Rate Limits](rate-limits/virtuagym-rate-limits.yml)
- [Fin Ops](finops/virtuagym-finops.yml)
- [Blog](https://business.virtuagym.com/blog/)

## Artifacts

- [OpenAPI](openapi/virtuagym-openapi.yml)
- [Postman Collection](collections/virtuagym.postman_collection.json)
- [Open Collection](collections/virtuagym.opencollection.json)
- [Review](review.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
