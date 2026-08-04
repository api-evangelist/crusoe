---
name: Deploy a model on the Crusoe Intelligence Foundry
description: List available models and GPU flavors, create a reserved-capacity self-serve inference deployment, watch its progress, and manage LoRA adapters.
api: openapi/crusoe-cloud-api-gateway-v1-openapi.json
generated: '2026-08-04'
method: generated
operations:
  - listFoundryDeployedModels
  - listFoundryFlavors
  - createFoundryDeployment
  - getFoundryDeployment
  - listFoundryDeployments
  - getFoundryDeploymentProgress
  - streamFoundryDeploymentProgress
  - getFoundryDeploymentActivity
  - updateFoundryDeployment
  - deleteFoundryDeployment
  - listFoundryLoras
  - getFoundryLora
  - createFoundryLora
  - deleteFoundryLora
  - listFoundryCredentials
  - createFoundryCredential
---

# Deploy a model on the Crusoe Intelligence Foundry

Base URL `https://api.cloud.crusoe.ai/v1`, project-scoped. Auth as in
`authentication/crusoe-authentication.yml`.

Two different things live under "inference" at Crusoe, and an agent must not confuse them:

- **Serverless Inference** — the OpenAI-compatible endpoint at `https://api.inference.crusoecloud.com/v1`,
  authenticated with a separate *Inference API key* (plain bearer, not the signed request). Pay per
  token, shared capacity. There is no anonymous machine-readable contract for it; every path on that
  host, including `/.well-known/*`, returns 401.
- **Self-serve deployments** — reserved capacity you provision through the operations below on the
  Crusoe Cloud API Gateway.

## Steps

1. **See what you can run.** `listFoundryDeployedModels`
   (`GET /projects/{project_id}/foundry/deployed-models`) returns each model's architecture, context
   length, quantization, region, availability and billing mode.
2. **Pick a GPU flavor.** `listFoundryFlavors`
   (`GET /projects/{project_id}/foundry/selfserve/flavors`) returns `flavor_type`, `gpu_type`,
   `gpus_per_instance`, `quantization`, `lora_suitable`, and `price_per_hour`. Read the price before
   you deploy.
3. **Create the deployment.** `createFoundryDeployment`
   (`POST /projects/{project_id}/foundry/selfserve/deployments`) requires `deployment_name`,
   `fine_tuned_model`, and `flavor_id`; `replicas` is optional. This returns **202 Accepted** with an
   id and status — it is asynchronous.
4. **Watch it come up.** `getFoundryDeploymentProgress`, or `streamFoundryDeploymentProgress` for the
   streaming variant. `getFoundryDeploymentActivity` shows activity once it is serving.
5. **Manage it.** `getFoundryDeployment`, `listFoundryDeployments`, `updateFoundryDeployment` (e.g. to
   change replica count), `deleteFoundryDeployment`.

## LoRA adapters

`createFoundryLora` registers a fine-tuned LoRA adapter; `listFoundryLoras`, `getFoundryLora`, and
`deleteFoundryLora` manage them. A `LoRAAdapterDeployment` carries `finetuning_job_id`,
`parent_model_name`, `rank`, `serving_endpoint_name`, and `status`. Only flavors marked
`lora_suitable` can serve them.

## Rules an agent must follow

- **Reserved capacity bills per hour, per replica.** `createFoundryDeployment` and any
  `updateFoundryDeployment` that raises `replicas` are consequential spend actions — confirm with a
  human first, and quote `price_per_hour` from the flavor.
- **Do not leave orphaned deployments.** If a create is retried after a timeout, call
  `listFoundryDeployments` and match on `deployment_name` before creating again — there is no
  idempotency key.
- **Vendor credentials are secrets.** `createFoundryCredential` / `updateFoundryCredential` store
  third-party credentials against the project. Never echo the response body into a transcript.
- `deleteFoundryDeployment` terminates serving traffic — treat as destructive.
