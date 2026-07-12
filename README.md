# Virtuagym (virtuagym)

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
