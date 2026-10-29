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

Crusoe is a vertically integrated "AI factory" company that designs, builds, and operates energy-first AI infrastructure, and sells it as Crusoe Cloud — a GPU cloud for training, fine-tuning, and inference. The public developer surface is the Crusoe Cloud API Gateway, a REST API at api.cloud.crusoe.ai covering virtual machines, instance groups and templates, block storage disks and snapshots, S3-compatible object storage, custom images, a container registry, VPC networking and load balancers, InfiniBand partitions and NVLink domains, Crusoe Managed Kubernetes and Slurm clusters, capacity reservations, IAM role bindings, SCIM/SSO, quotas, audit logs, usage and billing. Alongside it, the Intelligence Foundry exposes an OpenAI-compatible Managed Inference API for serverless inference, serverless fine-tuning, and self-serve deployments of open models. Crusoe also ships a first-party CLI, a Terraform provider, a Go API client, and a read-only Crusoe Cloud MCP server for AI assistants. Founded 2018, headquartered in Denver, Colorado.

**Areas:** AI Infrastructure · Cloud Computing · GPU Compute · Machine Learning · Inference · Kubernetes · Object Storage · Infrastructure-as-a-Service · Energy · MCP

## Crusoe on APIs.io

Everything profiled for Crusoe is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/crusoe/](https://apis.io/providers/crusoe/)** — or go straight to one of the APIs or properties below.

### APIs (64)

- [Crusoe Managed Inference API](https://apis.io/apis/crusoe/crusoe-managed-inference-api/) — OpenAI-compatible inference API from the Crusoe Intelligence Foundry. Send chat/completions and embeddings requests to Crusoe-hosted open models (DeepSeek,…
- [Crusoe Cloud MCP Server](https://apis.io/apis/crusoe/crusoe-cloud-mcp-server/) — First-party, read-only Model Context Protocol server published by Crusoe as the npm package @crusoeai/cloud-mcp and as a downloadable Claude Desktop…
- [Crusoe Audit Logs API](https://apis.io/apis/crusoe/crusoe-audit-logs-api/) — The Audit Logs API from Crusoe — 1 operation(s) for audit logs.
- [Crusoe AutoCluster Operations API](https://apis.io/apis/crusoe/crusoe-autocluster-operations-api/) — The AutoCluster Operations API from Crusoe — 2 operation(s) for autocluster operations.
- [Crusoe Auto Clusters API](https://apis.io/apis/crusoe/crusoe-autoclusters-api/) — The AutoClusters API from Crusoe — 2 operation(s) for autoclusters.
- [Crusoe Billing API](https://apis.io/apis/crusoe/crusoe-billing-api/) — The Billing API from Crusoe — 3 operation(s) for billing.
- [Crusoe Capacities API](https://apis.io/apis/crusoe/crusoe-capacities-api/) — The Capacities API from Crusoe — 1 operation(s) for capacities.
- [Crusoe Ccr API](https://apis.io/apis/crusoe/crusoe-ccr-api/) — The Ccr API from Crusoe — 8 operation(s) for ccr.
- [Crusoe Container Registry API](https://apis.io/apis/crusoe/crusoe-container-registry-api/) — The Container Registry API from Crusoe — 8 operation(s) for container registry.
- [Crusoe Custom Image Operations API](https://apis.io/apis/crusoe/crusoe-custom-image-operations-api/) — The Custom Image Operations API from Crusoe — 2 operation(s) for custom image operations.
- [Crusoe Custom Images API](https://apis.io/apis/crusoe/crusoe-customimages-api/) — The CustomImages API from Crusoe — 3 operation(s) for customimages.
- [Crusoe Disk Operations API](https://apis.io/apis/crusoe/crusoe-disk-operations-api/) — The Disk Operations API from Crusoe — 2 operation(s) for disk operations.
- [Crusoe Disks API](https://apis.io/apis/crusoe/crusoe-disks-api/) — The Disks API from Crusoe — 2 operation(s) for disks.
- [Crusoe Entities API](https://apis.io/apis/crusoe/crusoe-entities-api/) — The Entities API from Crusoe — 1 operation(s) for entities.
- [Crusoe Feature Flags API](https://apis.io/apis/crusoe/crusoe-feature-flags-api/) — The Feature Flags API from Crusoe — 1 operation(s) for feature flags.
- [Crusoe Foundry API](https://apis.io/apis/crusoe/crusoe-foundry-api/) — The Foundry API from Crusoe — 16 operation(s) for foundry.
- [Crusoe IB Networks API](https://apis.io/apis/crusoe/crusoe-ib-networks-api/) — The IB Networks API from Crusoe — 2 operation(s) for ib networks.
- [Crusoe IB Partitions API](https://apis.io/apis/crusoe/crusoe-ib-partitions-api/) — The IB Partitions API from Crusoe — 2 operation(s) for ib partitions.
- [Crusoe Identities API](https://apis.io/apis/crusoe/crusoe-identities-api/) — The Identities API from Crusoe — 1 operation(s) for identities.
- [Crusoe Images API](https://apis.io/apis/crusoe/crusoe-images-api/) — The Images API from Crusoe — 2 operation(s) for images.
- [Crusoe Instance Groups API](https://apis.io/apis/crusoe/crusoe-instance-groups-api/) — The Instance Groups API from Crusoe — 2 operation(s) for instance groups.
- [Crusoe Instance Templates API](https://apis.io/apis/crusoe/crusoe-instance-templates-api/) — The Instance Templates API from Crusoe — 2 operation(s) for instance templates.
- [Crusoe Internal Load Balancer Operations API](https://apis.io/apis/crusoe/crusoe-internal-load-balancer-operations-api/) — The Internal Load Balancer Operations API from Crusoe — 2 operation(s) for internal load balancer operations.
- [Crusoe Internal Load Balancers API](https://apis.io/apis/crusoe/crusoe-internal-load-balancers-api/) — The Internal Load Balancers API from Crusoe — 2 operation(s) for internal load balancers.
- [Crusoe Kubernetes Cluster Operations API](https://apis.io/apis/crusoe/crusoe-kubernetes-cluster-operations-api/) — The Kubernetes Cluster Operations API from Crusoe — 2 operation(s) for kubernetes cluster operations.
- [Crusoe Kubernetes Clusters API](https://apis.io/apis/crusoe/crusoe-kubernetes-clusters-api/) — The Kubernetes Clusters API from Crusoe — 3 operation(s) for kubernetes clusters.
- [Crusoe Kubernetes Node Pool Operations API](https://apis.io/apis/crusoe/crusoe-kubernetes-node-pool-operations-api/) — The Kubernetes Node Pool Operations API from Crusoe — 2 operation(s) for kubernetes node pool operations.
- [Crusoe Kubernetes Node Pools API](https://apis.io/apis/crusoe/crusoe-kubernetes-node-pools-api/) — The Kubernetes Node Pools API from Crusoe — 5 operation(s) for kubernetes node pools.
- [Crusoe Kubernetes Support Access API](https://apis.io/apis/crusoe/crusoe-kubernetes-support-access-api/) — The Kubernetes Support Access API from Crusoe — 1 operation(s) for kubernetes support access.
- [Crusoe Kubernetes Versions API](https://apis.io/apis/crusoe/crusoe-kubernetes-versions-api/) — The Kubernetes Versions API from Crusoe — 1 operation(s) for kubernetes versions.
- [Crusoe Limited Usage API Key API](https://apis.io/apis/crusoe/crusoe-limitedusageapikey-api/) — The LimitedUsageAPIKey API from Crusoe — 1 operation(s) for limitedusageapikey.
- [Crusoe Load Balancer Operations API](https://apis.io/apis/crusoe/crusoe-load-balancer-operations-api/) — The Load Balancer Operations API from Crusoe — 2 operation(s) for load balancer operations.
- [Crusoe Load Balancers API](https://apis.io/apis/crusoe/crusoe-load-balancers-api/) — The Load Balancers API from Crusoe — 2 operation(s) for load balancers.
- [Crusoe Locations API](https://apis.io/apis/crusoe/crusoe-locations-api/) — The Locations API from Crusoe — 1 operation(s) for locations.
- [Crusoe MFA API](https://apis.io/apis/crusoe/crusoe-mfa-api/) — The MFA API from Crusoe — 1 operation(s) for mfa.
- [Crusoe NVLink Domains API](https://apis.io/apis/crusoe/crusoe-nvlink-domains-api/) — The NVLink Domains API from Crusoe — 1 operation(s) for nvlink domains.
- [Crusoe Observability API](https://apis.io/apis/crusoe/crusoe-observability-api/) — The Observability API from Crusoe — 5 operation(s) for observability.
- [Crusoe Projects API](https://apis.io/apis/crusoe/crusoe-projects-api/) — The Projects API from Crusoe — 2 operation(s) for projects.
- [Crusoe Quotas API](https://apis.io/apis/crusoe/crusoe-quotas-api/) — The Quotas API from Crusoe — 2 operation(s) for quotas.
- [Crusoe Reservations API](https://apis.io/apis/crusoe/crusoe-reservations-api/) — The Reservations API from Crusoe — 4 operation(s) for reservations.
- [Crusoe Role Bindings API](https://apis.io/apis/crusoe/crusoe-rolebindings-api/) — The RoleBindings API from Crusoe — 2 operation(s) for rolebindings.
- [Crusoe Roles API](https://apis.io/apis/crusoe/crusoe-roles-api/) — The Roles API from Crusoe — 1 operation(s) for roles.
- [Crusoe SCIM API](https://apis.io/apis/crusoe/crusoe-scim-api/) — The SCIM API from Crusoe — 4 operation(s) for scim.
- [Crusoe Slurm Cluster Operations API](https://apis.io/apis/crusoe/crusoe-slurm-cluster-operations-api/) — The Slurm Cluster Operations API from Crusoe — 2 operation(s) for slurm cluster operations.
- [Crusoe Slurm Clusters API](https://apis.io/apis/crusoe/crusoe-slurm-clusters-api/) — The Slurm Clusters API from Crusoe — 2 operation(s) for slurm clusters.
- [Crusoe Slurm Nodeset Operations API](https://apis.io/apis/crusoe/crusoe-slurm-nodeset-operations-api/) — The Slurm Nodeset Operations API from Crusoe — 2 operation(s) for slurm nodeset operations.
- [Crusoe Slurm Nodesets API](https://apis.io/apis/crusoe/crusoe-slurm-nodesets-api/) — The Slurm Nodesets API from Crusoe — 2 operation(s) for slurm nodesets.
- [Crusoe Snapshot Operations API](https://apis.io/apis/crusoe/crusoe-snapshot-operations-api/) — The Snapshot Operations API from Crusoe — 2 operation(s) for snapshot operations.
- [Crusoe Snapshots API](https://apis.io/apis/crusoe/crusoe-snapshots-api/) — The Snapshots API from Crusoe — 2 operation(s) for snapshots.
- [Crusoe SSH Keys API](https://apis.io/apis/crusoe/crusoe-ssh-keys-api/) — The SSH Keys API from Crusoe — 1 operation(s) for ssh keys.
- [Crusoe SSO API](https://apis.io/apis/crusoe/crusoe-sso-api/) — The SSO API from Crusoe — 3 operation(s) for sso.
- [Crusoe Tokens API](https://apis.io/apis/crusoe/crusoe-tokens-api/) — The Tokens API from Crusoe — 1 operation(s) for tokens.
- [Crusoe Usage API](https://apis.io/apis/crusoe/crusoe-usage-api/) — The Usage API from Crusoe — 3 operation(s) for usage.
- [Crusoe VM Operations API](https://apis.io/apis/crusoe/crusoe-vm-operations-api/) — The VM Operations API from Crusoe — 2 operation(s) for vm operations.
- [Crusoe VPC Firewall Rule Operations API](https://apis.io/apis/crusoe/crusoe-vpc-firewall-rule-operations-api/) — The VPC Firewall Rule Operations API from Crusoe — 2 operation(s) for vpc firewall rule operations.
- [Crusoe VPC Firewall Rules API](https://apis.io/apis/crusoe/crusoe-vpc-firewall-rules-api/) — The VPC Firewall Rules API from Crusoe — 2 operation(s) for vpc firewall rules.
- [Crusoe VPC Network Operations API](https://apis.io/apis/crusoe/crusoe-vpc-network-operations-api/) — The VPC Network Operations API from Crusoe — 2 operation(s) for vpc network operations.
- [Crusoe VPC Networks API](https://apis.io/apis/crusoe/crusoe-vpc-networks-api/) — The VPC Networks API from Crusoe — 2 operation(s) for vpc networks.
- [Crusoe VPC Subnet Operations API](https://apis.io/apis/crusoe/crusoe-vpc-subnet-operations-api/) — The VPC Subnet Operations API from Crusoe — 2 operation(s) for vpc subnet operations.
- [Crusoe VPC Subnets API](https://apis.io/apis/crusoe/crusoe-vpc-subnets-api/) — The VPC Subnets API from Crusoe — 2 operation(s) for vpc subnets.
- [Crusoe Cloud API](https://apis.io/apis/crusoe/cloud-api/) — The Crusoe Cloud API is the primary control plane for provisioning and managing GPU compute, storage, networking, Kubernetes clusters, identity, and billing…
- [Crusoe V Ms API](https://apis.io/apis/crusoe/crusoe-vms-api/) — The VMs API from Crusoe — 6 operation(s) for vms.
- [Crusoe S3 Buckets API](https://apis.io/apis/crusoe/crusoe-s3-buckets-api/) — The S3 Buckets API from Crusoe — 7 operation(s) for s3 buckets.
- [Crusoe S3 Keys API](https://apis.io/apis/crusoe/crusoe-s3-keys-api/) — The S3 Keys API from Crusoe — 2 operation(s) for s3 keys.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Crusoe Webhooks](https://apis.io/asyncapis/crusoe/crusoe-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [crusoe-cloud](https://apis.io/servers/crusoe/crusoe-cloud/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Crusoe Agentic Access](https://apis.io/agentic-access/crusoe/crusoe-agentic-access/)

#### Collections (61)

Postman and Open Collection request collections.

- [Crusoe Audit Logs API](https://apis.io/collections/crusoe/open-crusoe-audit-logs-api/)
- [Crusoe AutoCluster Operations API](https://apis.io/collections/crusoe/open-crusoe-autocluster-operations-api/)
- [Crusoe Auto Clusters API](https://apis.io/collections/crusoe/open-crusoe-autoclusters-api/)
- [Crusoe Billing API](https://apis.io/collections/crusoe/open-crusoe-billing-api/)
- [Crusoe Capacities API](https://apis.io/collections/crusoe/open-crusoe-capacities-api/)
- [Crusoe Ccr API](https://apis.io/collections/crusoe/open-crusoe-ccr-api/)
- [Crusoe Container Registry API](https://apis.io/collections/crusoe/open-crusoe-container-registry-api/)
- [Crusoe Custom Image Operations API](https://apis.io/collections/crusoe/open-crusoe-custom-image-operations-api/)
- [Crusoe Custom Images API](https://apis.io/collections/crusoe/open-crusoe-customimages-api/)
- [Crusoe Disk Operations API](https://apis.io/collections/crusoe/open-crusoe-disk-operations-api/)
- [Crusoe Disks API](https://apis.io/collections/crusoe/open-crusoe-disks-api/)
- [Crusoe Entities API](https://apis.io/collections/crusoe/open-crusoe-entities-api/)
- [Crusoe Feature Flags API](https://apis.io/collections/crusoe/open-crusoe-feature-flags-api/)
- [Crusoe Foundry API](https://apis.io/collections/crusoe/open-crusoe-foundry-api/)
- [Crusoe IB Networks API](https://apis.io/collections/crusoe/open-crusoe-ib-networks-api/)
- [Crusoe IB Partitions API](https://apis.io/collections/crusoe/open-crusoe-ib-partitions-api/)
- [Crusoe Identities API](https://apis.io/collections/crusoe/open-crusoe-identities-api/)
- [Crusoe Images API](https://apis.io/collections/crusoe/open-crusoe-images-api/)
- [Crusoe Instance Groups API](https://apis.io/collections/crusoe/open-crusoe-instance-groups-api/)
- [Crusoe Instance Templates API](https://apis.io/collections/crusoe/open-crusoe-instance-templates-api/)
- [Crusoe Internal Load Balancer Operations API](https://apis.io/collections/crusoe/open-crusoe-internal-load-balancer-operations-api/)
- [Crusoe Internal Load Balancers API](https://apis.io/collections/crusoe/open-crusoe-internal-load-balancers-api/)
- [Crusoe Kubernetes Cluster Operations API](https://apis.io/collections/crusoe/open-crusoe-kubernetes-cluster-operations-api/)
- [Crusoe Kubernetes Clusters API](https://apis.io/collections/crusoe/open-crusoe-kubernetes-clusters-api/)
- [Crusoe Kubernetes Node Pool Operations API](https://apis.io/collections/crusoe/open-crusoe-kubernetes-node-pool-operations-api/)
- …and 36 more published on APIs.io

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Crusoe Cloud Api Gateway V1 Overlay](https://apis.io/overlays/crusoe/crusoe-cloud-api-gateway-v1-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Crusoe Authentication](https://apis.io/security/crusoe/crusoe-authentication/)
- [Crusoe Domain Security](https://apis.io/security/crusoe/crusoe-domain-security/)
- [Crusoe Trust Center](https://apis.io/security/crusoe/crusoe-trust-center/)
- [Crusoe Vulnerability Disclosure](https://apis.io/security/crusoe/crusoe-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Crusoe Plans Pricing](https://apis.io/plans/crusoe/crusoe-plans-pricing/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.crusoe.ai/)
- [Documentation](https://docs.crusoecloud.com/)
- [Getting started](https://docs.crusoecloud.com/quickstart/overview)
- [API reference](https://docs.crusoecloud.com/api/)
- [Pricing](https://www.crusoe.ai/cloud/pricing)
- [Sign up](https://console.crusoecloud.com/signup)
- [Support](https://docs.crusoecloud.com/resources/support)
- [Blog](https://www.crusoe.ai/resources/blog)
- [Security](https://www.crusoe.ai/.well-known/security.txt)
- [Compliance](https://trust.crusoe.ai/)
- [Terms of service](https://legal.crusoe.ai/#terms-of-service)
- [Privacy policy](https://legal.crusoe.ai/#cloud-privacy-policy)
- [GitHub](https://github.com/crusoecloud)
- [Status](https://status.crusoecloud.com)

## API Evangelist rating

**Kin Score 57.4** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 51.4 |
| Contract governance | 4.5 |
| Operational transparency | 55.3 |
| Developer ergonomics | 73.2 |
| Access clarity | 68.4 |

**Agent readiness 33.6** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
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
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 24.6** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/crusoe/](https://apis.io/providers/crusoe/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Crusoe: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/crusoe/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
