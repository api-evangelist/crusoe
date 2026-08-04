---
name: Launch a GPU VM on Crusoe Cloud
description: Check capacity, pick an image, create a virtual machine in a Crusoe Cloud project, and poll the async operation until the instance is running.
api: openapi/crusoe-cloud-api-gateway-v1-openapi.json
generated: '2026-08-04'
method: generated
operations:
  - listLocations
  - listSliceCapacities
  - listImages
  - createInstance
  - getComputeVMsInstancesOperation
  - getInstance
  - listInstances
---

# Launch a GPU VM on Crusoe Cloud

Base URL `https://api.cloud.crusoe.ai/v1`. Every step below is a real operation in the published
Swagger document; nothing here is invented.

## Before you start

- **Authenticate every request.** The API uses a signed bearer token: send
  `Authorization: Bearer <version:access_key_id:base64_encoded_signature>` **and**
  `X-Crusoe-Timestamp: <RFC 3339 timestamp>`. The signature is an HMAC-SHA256 over
  `http_path\ncanonicalized_query_params\nhttp_verb\ntimestamp_header_value`, keyed with the
  raw-urlsafe-base64-decoded secret key, base64 encoded, signature version `1.0`.
  See `authentication/crusoe-authentication.yml`. The OpenAPI does **not** declare this — do not expect
  a generated client to authenticate on its own.
- **You need a `project_id`.** Call `listProjects` and pick one; nearly every operation is
  project-scoped.

## Steps

1. **See where you can run.** `listLocations` returns the available locations.
2. **Check capacity for the GPU type you want.** `listSliceCapacities` (`GET /capacities`) takes
   optional `product_name` and `location` query parameters. Do this first — GPU availability is the
   binding constraint, and a create call against an unavailable type will fail.
3. **Pick an image.** `listImages` returns the curated public images; `getImage` fetches one.
   For a project-owned image use `listCustomImages` / `getCustomImage`.
4. **Create the VM.** `createInstance`
   (`POST /projects/{project_id}/compute/vms/instances`). The request body requires
   `type`, `ssh_public_key`, `name`, and `location`. Optional fields include `image`,
   `custom_image`, `disks`, `network_interfaces`, `startup_script`, `shutdown_script`,
   `reservation_specification`, `nvlink_domain_id`, `host_channel_adapters`, `maintenance_policy`, and
   `install_crusoe_watch_agent`. To launch many at once use `bulkCreateInstance` instead.
5. **Poll the operation.** The create returns an async operation, not a finished VM. Poll
   `getComputeVMsInstancesOperation`
   (`GET /projects/{project_id}/compute/vms/instances/operations/{operation_id}`) until it reaches a
   terminal state. `listComputeVMsInstancesOperations` lists operations in flight.
6. **Confirm the instance.** `getInstance` for the single VM, or `listInstances` for the project.

## Rules an agent must follow

- **There is no idempotency key.** `createInstance` is not safe to blind-retry — a retry after a
  timeout can create a second VM that bills. On an ambiguous failure, call `listInstances` and match on
  `name` before retrying.
- **Errors are flat.** Failures return `{ "code": "<http status>", "message": "<snake_case reason>" }`
  — e.g. `401 bad_credential`, `403 unauthorized`, `400 bad_request`. There is no application-level
  error code, so branch on HTTP status plus `message`. See `errors/crusoe-problem-types.yml`.
- **No rate-limit headers.** The API publishes no `X-RateLimit-*` or `Retry-After` contract; back off
  exponentially on 5xx and check organization and project quotas with `listOrgQuotas` /
  `listProjectQuotas` before scaling up.
- **Creating GPU VMs spends money.** Treat step 4 as a consequential action requiring explicit
  confirmation. See `agentic-access/crusoe-agentic-access.yml`.

## Related

- Storage: `skills/crusoe-manage-block-storage.md`
- Clusters: `skills/crusoe-provision-kubernetes-cluster.md`
- Cost: `skills/crusoe-audit-usage-and-quotas.md`
