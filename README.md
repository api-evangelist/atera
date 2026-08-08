# Atera

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Atera Networks Ltd. operates an all-in-one IT management platform combining remote
monitoring and management (RMM), professional services automation (PSA), helpdesk and
ticketing, patch management, network discovery, remote access, reporting and billing in
a single per-technician subscription used by managed service providers and internal IT
departments. Its AI layer adds Action AI, AI Copilot and Robin (IT Autopilot), plus an
AI Center that installs Model Context Protocol (MCP) integrations from a catalog or
registers custom MCP servers.

## API surface

| | |
|---|---|
| REST API | `https://app.atera.com/api/v3` |
| Reference | <https://app.atera.com/apidocs> — **HTTP 401, empty body, to any unauthenticated client** |
| Docs | <https://support.atera.com/hc/en-us/articles/219083397-Using-the-Atera-API> |
| Auth | Account token in the `X-API-KEY` header; per-domain Read/Write/Delete permissions, IP allowlist, expiry (max 1 year) |
| Data domains | Agents, Alerts, Billing, Contacts, Contracts, Customers, CustomValues, Departments, Devices, KnowledgeBase, Rates, Tickets |
| Events | Webhooks on three ticket triggers only (Enterprise / Superpower tiers) |
| Status | <https://status.atera.com> — "API Service" is a first-class component |
| Trust | <https://trust.atera.com/> (Vanta) |

## What this profile found

Atera states in its own API FAQ that "Atera employs OpenAPI 3.0 to drive its API" — but
that document is served only to an authenticated tenant. Contract discovery was run
against every host (`app.atera.com`, `www.atera.com`, `api.atera.com`,
`developers.atera.com`) across `/openapi.json`, `/swagger/docs/v{1,2,3}`,
`/swagger/v1/swagger.json`, `/api-docs`, `/.well-known/*` and `/llms.txt`. Nothing
anonymously readable came back: 404s, 401s with empty bodies, and three zero-byte
soft-200s under `/swagger/` that are the ASP.NET catch-all, not a specification.

The human documentation is good and public. The machine-readable contract is not
published at all. That gap — a real OpenAPI 3.0 that exists but never leaves the tenant
login — is the single highest-value thing Atera could change.

Also recorded: no first-party SDK in any registry (Atera's own docs send readers to the
community PowerShell module `PSAtera`), no idempotency contract, no documented rate
limit or 429 semantics, empty-bodied 4xx responses, no error registry, no
`/.well-known/` documents, no A2A agent card, and no MCP server (Atera consumes MCP, it
does not publish one). `www.atera.com` answers every automated request — including
`/robots.txt` — with a Cloudflare 403.

Artifacts in this repo: `authentication/`, `conventions/`, `errors/`, `lifecycle/`,
`changelog/`, `asyncapi/` (webhook catalog), `conformance/`, `packages/`, `security/`,
`well-known/`, `llms/`.
