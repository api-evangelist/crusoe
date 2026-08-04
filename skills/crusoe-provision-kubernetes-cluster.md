---
name: Provision a Crusoe Managed Kubernetes cluster with a GPU node pool
description: Create a CMK cluster, attach a GPU node pool, fetch kubeconfig credentials, and manage rotation and AutoClusters remediation.
api: openapi/crusoe-cloud-api-gateway-v1-openapi.json
generated: '2026-08-04'
method: generated
operations:
  - listKubernetesVersions
  - createCluster
  - getKubernetesClustersOperation
  - getCluster
  - listClusters
  - createNodePool
  - getKubernetesNodePoolsOperation
  - listNodePools
  - getNodePool
  - listKubernetesNodePoolVMs
  - getClusterCredentials
  - rotateNodePool
  - getNodePoolRotateStatus
  - cancelNodePoolRotate
  - getAutoClustersConfig
  - updateAutoClustersConfig
  - remediateVM
  - updateCluster
  - deleteNodePool
  - deleteCluster
---

# Provision a Crusoe Managed Kubernetes (CMK) cluster

Base URL `https://api.cloud.crusoe.ai/v1`. Auth as in `authentication/crusoe-authentication.yml`.

## Steps

1. **Pick a supported Kubernetes version.** `listKubernetesVersions`
   (`GET /projects/{project_id}/kubernetes/versions`).
2. **Create the control plane.** `createCluster` (`POST /projects/{project_id}/kubernetes/clusters`)
   requires `name`, `location`, and `version`. Optional: `subnet_id`, `private`, `cluster_cidr`,
   `service_cluster_ip_range`, `node_cidr_mask_size`, `add_ons`, `auth_config`, and the
   `apiserver_extra_args` / `controller_manager_extra_args` / `scheduler_extra_args` escape hatches.
3. **Poll it.** `getKubernetesClustersOperation` until terminal.
4. **Add a node pool.** `createNodePool` (`POST /projects/{project_id}/kubernetes/nodepools`) requires
   `name`, `product_name`, `count`, and `cluster_id`. Optional: `subnet_id`, `ib_partition_id`,
   `nvlink_domain_id`, `reservation_specification`, `ssh_public_key`, `node_labels`, `node_taints`,
   `placement_policy`, `public_ip_type`, `ephemeral_storage_for_containerd`.
   Check GPU availability with `listSliceCapacities` before you size `count`.
5. **Poll it.** `getKubernetesNodePoolsOperation` until terminal, then `listKubernetesNodePoolVMs` to
   see the nodes.
6. **Get kubeconfig.** `getClusterCredentials`
   (`POST /projects/{project_id}/kubernetes/clusters/{cluster_id}/get-credentials`, optional
   `auth_type` query parameter).

## Day-2 operations

- **Rolling node replacement:** `rotateNodePool`, then `getNodePoolRotateStatus`;
  `cancelNodePoolRotate` to stop it.
- **Automated hardware remediation:** `getAutoClustersConfig` / `updateAutoClustersConfig` on the
  cluster; `remediateVM` to force remediation of one node. AutoClusters fires notifications on
  `node_replacement_initiated` / `completed` / `failed` and on detection-only XID codes — see
  `asyncapi/crusoe-webhooks.yml`.
- **Support access:** `getSupportSettings` / `updateSupportSettings` grant or revoke Crusoe support
  engineers direct access to the cluster.

## Rules an agent must follow

- **`deleteCluster` and `deleteNodePool` destroy running workloads.** Require explicit human
  confirmation; never issue them as part of a retry or cleanup heuristic.
- **`rotateNodePool` and `remediateVM` are disruptive.** They drain and replace nodes.
- **No idempotency key.** Reconcile with `listClusters` / `listNodePools` by `name` before retrying a
  create.
- Poll operations rather than assuming completion; a cluster is not usable until its operation is
  terminal.
