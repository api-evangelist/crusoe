# Crusoe

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

Crusoe is a vertically integrated "AI factory" company that designs, builds, and operates energy-first
AI infrastructure, and sells it as **Crusoe Cloud** — a GPU cloud for training, fine-tuning, and
inference. Founded 2018, headquartered in Denver, Colorado.

## API surface

| API | Base URL | Contract |
|---|---|---|
| Crusoe Cloud API Gateway | `https://api.cloud.crusoe.ai/v1` | Swagger 2.0, 150 paths / 232 operations ([v1](https://api.cloud.crusoe.ai/v1/openapi.json), [v1alpha5](https://api.cloud.crusoe.ai/v1alpha5/openapi.json)) |
| Crusoe Managed Inference API | `https://api.inference.crusoecloud.com/v1` | OpenAI-compatible; auth-gated, no anonymous contract |
| Crusoe Cloud MCP Server | `npx -y @crusoeai/cloud-mcp` | stdio, read-only, 41 documented tools (preview) |

## Links

- Developers: https://www.crusoe.ai/developers
- Documentation: https://docs.crusoecloud.com/
- API reference: https://docs.crusoecloud.com/api/
- Changelog: https://docs.crusoecloud.com/resources/changelog
- Status: https://status.crusoecloud.com
- Trust center: https://trust.crusoe.ai/
- GitHub: https://github.com/crusoecloud
- Pricing: https://www.crusoe.ai/cloud/pricing
- Legal: https://legal.crusoe.ai/

## What this profile captures

`openapi/` (both published Swagger tracks, verbatim) · `llms/` (Crusoe's own `llms.txt` from the docs
and marketing hosts, verbatim) · `mcp/` (the published MCP server + a crosswalk binding its 41 tools to
backing `operationId`s) · `authentication/` · `conventions/` · `errors/` · `data-model/` ·
`lifecycle/` · `changelog/` · `conformance/` · `asyncapi/` (the notification/webhook catalog) ·
`packages/` · `cli/` · `security/` · `well-known/` · `skills/` · `agentic-access/` · `overlays/`.

## Notable gaps

- The published Swagger documents declare **no `securityDefinitions`** at all, even though 221 of 232
  operations return a 401. A generated client cannot authenticate from the contract.
- Swagger 2.0 rather than OpenAPI 3.x.
- **No idempotency contract** on any create operation.
- Errors are a flat `{code, message}` envelope with no application-level code vocabulary, and the
  Observability endpoints return a *different* gRPC-gateway envelope.
- Webhooks are documented but have **no AsyncAPI, no payload schemas, no signature scheme**, and cannot
  be provisioned through the API.
- No A2A agent card on any Crusoe host.
