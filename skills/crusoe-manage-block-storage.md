---
name: Create, attach, resize and snapshot Crusoe Cloud block storage
description: Provision a Crusoe Cloud disk, attach it to a VM, resize it, and take a point-in-time snapshot, polling the async storage operations throughout.
api: openapi/crusoe-cloud-api-gateway-v1-openapi.json
generated: '2026-08-04'
method: generated
operations:
  - createDisk
  - listDisks
  - getDisk
  - resizeDisk
  - updateInstanceAttachDisks
  - updateInstanceDetachDisks
  - createDiskSnapshot
  - listDiskSnapshots
  - getDiskSnapshot
  - renameDiskSnapshot
  - deleteDiskSnapshot
  - deleteDisk
  - getStorageDisksOperation
  - getStorageSnapshotsOperation
---

# Manage Crusoe Cloud block storage

Base URL `https://api.cloud.crusoe.ai/v1`. Auth as described in
`authentication/crusoe-authentication.yml`. All operations are project-scoped.

## Steps

1. **Create a disk.** `createDisk` (`POST /projects/{project_id}/storage/disks`). Only `name` is
   required; `size`, `type`, `block_size`, `location`, and `snapshot_id` are optional. Pass
   `snapshot_id` to restore from an existing snapshot instead of provisioning empty.
2. **Poll the storage operation.** `getStorageDisksOperation`
   (`GET /projects/{project_id}/storage/disks/operations/{operation_id}`) until terminal.
   `listStorageDisksOperations` lists in-flight disk operations.
3. **Attach it to a VM.** `updateInstanceAttachDisks`
   (`POST /projects/{project_id}/compute/vms/instances/{vm_id}/attach-disks`), body `attach_disks`.
   Detach with `updateInstanceDetachDisks`.
4. **Resize when needed.** `resizeDisk` (`PATCH /projects/{project_id}/storage/disks/{disk_id}`).
5. **Snapshot it.** `createDiskSnapshot` (`POST /projects/{project_id}/storage/snapshots`) requires
   `disk_id` and `name`. Poll `getStorageSnapshotsOperation`. Manage snapshots with
   `listDiskSnapshots`, `getDiskSnapshot`, `renameDiskSnapshot`, `deleteDiskSnapshot`.
6. **Inspect.** `listDisks` / `getDisk`. A disk's `attached_to` field tells you which instance holds
   it; an instance's `disks` array is the other side of the same relationship
   (`data-model/crusoe-data-model.yml`).

## Rules an agent must follow

- **Detach before delete.** `deleteDisk` on an attached disk is not safe; check `attached_to` first.
- **Deletes are destructive and unrecoverable.** `deleteDisk` and `deleteDiskSnapshot` require explicit
  human confirmation.
- **No idempotency key.** A retried `createDisk` or `createDiskSnapshot` can create a duplicate that
  bills. Reconcile with `listDisks` / `listDiskSnapshots` by `name` before retrying.
- **Async, not synchronous.** Never treat a 200 from a create/resize as "done" — poll the matching
  `*Operation` endpoint.

## Object storage is a different surface

S3-compatible object storage is separate from block storage: `listS3Buckets`, `getS3Bucket`,
`createS3Bucket`, `enableS3BucketVersioning`, `enableS3BucketObjectLock`, `updateS3BucketTags`,
`deleteS3Bucket`, plus organization-level keys via `listS3Keys` / `createS3Key` / `deleteS3Key`.
