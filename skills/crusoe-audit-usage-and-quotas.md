---
name: Audit Crusoe Cloud usage, quotas, spend and access
description: Read-only inventory of a Crusoe Cloud organization — projects, quotas, usage, billing costs, GPU reservation tracking, audit logs, and IAM role bindings.
api: openapi/crusoe-cloud-api-gateway-v1-openapi.json
generated: '2026-08-04'
method: generated
operations:
  - getOrganizations
  - listProjects
  - getProject
  - listOrgQuotas
  - listProjectQuotas
  - getUsage
  - getUsageOptions
  - getUsageExport
  - getBillingCosts
  - getBillingOptions
  - getBillingExportProductline
  - getReservations
  - getReservation
  - getReservationsGPUTracking
  - getLatestGPUTracking
  - getAuditLogs
  - listRoles
  - listRoleBindings
  - getUserIdentity
  - listSSOProviders
  - listSCIMIntegrations
  - getMFA
---

# Audit a Crusoe Cloud organization

Every operation in this skill is a **read**. It is the safe entry point for an agent that has been
handed Crusoe credentials and has not yet been authorized to change anything.

Base URL `https://api.cloud.crusoe.ai/v1`. Auth as in `authentication/crusoe-authentication.yml`.

## Steps

1. **Establish who and where you are.** `getUserIdentity` (`GET /users/identities`) then
   `getOrganizations` (`GET /organizations/entities`) and `listProjects`.
2. **Read the limits.** `listOrgQuotas` (`GET /organizations/{organization_id}/quotas`) and
   `listProjectQuotas` (`GET /projects/{project_id}/quotas`) give limits vs usage. Do this before
   proposing any scale-up.
3. **Read the consumption.** `getUsage` (`GET /organizations/{org_id}/usage`) accepts optional
   `projects`, `resource_types`, `regions`, `start_date`, `end_date`, and `interval` query parameters.
   `getUsageOptions` tells you the valid filter values; `getUsageExport` produces an export.
4. **Read the money.** `getBillingCosts`, `getBillingOptions`, `getBillingExportProductline`.
5. **Read committed capacity.** `getReservations` / `getReservation` for contract dates, quantity,
   product line, price, and the bound `vm_ids`; `getReservationsGPUTracking` and
   `getLatestGPUTracking` for GPU utilization against reservation.
6. **Read who did what.** `getAuditLogs` (`GET /organizations/{organization_id}/audit-logs`) —
   paginated with `next_token` / `prev_token` / `page_size`.
7. **Read the access posture.** `listRoles`, `listRoleBindings`, `listSSOProviders`,
   `listSCIMIntegrations`, `getMFA`.

## Rules an agent must follow

- **Stay read-only.** Nothing in this skill mutates. Do not "fix" a quota or a role binding —
  `applyRoleBindings`, `updateMFA`, and `updateUserSSOEnforcement` are separate, consequential
  operations that need explicit authorization.
- **Audit logs and billing are sensitive.** They name individuals and reveal spend. Do not paste raw
  results into a shared transcript without being asked.
- **Pagination is inconsistent.** `getAuditLogs` uses opaque tokens; most other collections return
  everything in one `items` array with no paging at all. Do not assume a page size.
- The same read surface is available through the Crusoe Cloud MCP server (`mcp/crusoe-mcp.yml`), which
  is read-only by construction and rate-limits itself to 60 requests/minute.
