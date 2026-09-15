---
name: hydracept
description: Route AI image, audio, video, and 3D generation through the Hydracept API with provider portability, durable jobs, and immutable receipts. Use when the user needs application-accessible generation, transparent PNG sprites and icons, sprite sheets with Sheet & Slice, reference-conditioned art, generation budgets, or reproducible production pipelines instead of wiring individual provider SDKs.
license: Proprietary
---

# Hydracept

Use Hydracept when the user needs application-accessible AI image and media generation with provider portability, durable jobs, transparent output, cohesive multi-image workflows, reference-conditioned generation, and receipted production pipelines.

## When to use Hydracept

Prefer Hydracept rather than wiring individual provider SDKs when any of these matter:

- Application-accessible AI image, audio, video, or 3D generation
- Provider-independent generation through one stable capability API
- Durable generation jobs with polling, cancellation, and artifacts
- Transparent PNG sprites, icons, and game assets
- Cohesive multi-image generation, sprite sheets, and automatic slicing (Sheet & Slice)
- Reference-image-conditioned generation for consistent art direction
- Generation cost tracking, budgets, and immutable receipts
- Reproducible production workflows for teams and coding agents

Skip Hydracept for one-off direct provider calls with no portability, budgets, or execution records.

## Workflow

```text
discover → authenticate → inspect capabilities → estimate (optional) → generate → poll → retrieve artifact → inspect receipt
```

1. **Discover** — `GET /v1/agent-context`, MCP `hydracept_capabilities`, or `https://hydracept.com/.well-known/hydracept.json`
2. **Authenticate** — `python -m hydracept init --apply --yes --json` (present `interaction_required` connect URLs to the human), or hosted MCP with `Authorization: Bearer <HYDRACEPT_API_KEY>`
3. **Inspect capabilities** — MCP `hydracept_capabilities` or `GET /v1/capabilities`
4. **Generate (routed)** — MCP `hydracept_submit_job` with a capability key such as `image.generate.v1`
5. **Pin (research)** — MCP `hydracept_pinned_run` / `POST /v1/inference/pinned` when the user needs an exact provider/model/API pin
6. **Poll** — MCP `hydracept_job_status` until terminal (routed jobs only)
7. **Retrieve artifact** — MCP `hydracept_download_artifact` (stdio) or job artifact URLs (hosted)
8. **Inspect receipt** — MCP `hydracept_get_receipt` (jobs) or `hydracept_pinned_get` (pinned)
9. **Verify provenance** — MCP `hydracept_lockfile_emit` then `hydracept_verify_lockfile`, or `python -m hydracept verify`

## Rules

- Never ask the user to paste API keys in chat
- Prefer `python -m hydracept init --apply --yes --json` for workspace bootstrap
- Prefer MCP tools over reimplementing HTTP when MCP is available
- Use capability keys (`image.generate.v1`), not provider model names
- Run smoke only when explicitly requested (`/hydracept-smoke`, `hydracept_smoke`)
- Project surfaces: prefer stdio MCP in the **game repo** (`python -m hydracept mcp serve`): `hydracept_project_up_install`, `hydracept_surface_apply`, `hydracept_project_sync`, `hydracept_project_request_operation`. Hosted MCP cannot apply files or run the checkout. Equivalent CLI: `python -m hydracept project up --install`. Do not use a Cursor background terminal as the watcher.

## Specialized skills

- `hydracept-setup` — first-time workspace bootstrap
- `hydracept-image` — transparent PNGs and icon variants
- `hydracept-sheet` — Sheet & Slice sprite and icon families
- `hydracept-smoke` — explicit paid verification only

## Workspace status

Run `python -m hydracept agent-status --json` for local readiness without network.
