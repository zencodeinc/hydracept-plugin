---
name: hydracept-init
description: Bootstrap Hydracept in this project with the canonical CLI init contract. Binds stdio MCP to workspace secrets.
---

# Hydracept init

Bootstrap Hydracept without asking the human to paste secrets into chat. `init` is the canonical first operation for a project checkout; do not prepend a separate login or doctor sequence.

## Preferred path (project checkout)

1. Check `python -m hydracept --help`. If missing, explain `pip install -U hydracept` and wait for approval.
2. Run `python -m hydracept init --apply --yes --json`.
3. If status is `interaction_required`, treat it as a **hard human boundary**, not an execution failure:
   - stop automation immediately; do not background `--wait` or continue with doctor, consumer-check, status, or other diagnostics;
   - preserve `bootstrapSessionId`, `expiresAt`, and `action.url`;
   - if `presentation.agentAction` is `present_and_yield` (or `interaction.surface` is `project.connect`) and `hydracept_interaction_surface` is available this turn, invoke that tool once with the supplied context and stop the turn;
   - otherwise show `action.url` **verbatim**; do not construct, shorten, replace, normalize, or guess the URL, then stop;
   - only after the human confirms completion, run the exact `afterCompletion.command` returned by init.
4. If a post-confirmation `--wait` run ends with `code: bootstrap_wait_timeout`, keep the same session and `action.url` until `expiresAt`. Do not mint a new activation just because local polling stopped.
5. Ready JSON includes `mcp` (`bound`, `transport: stdio`, `projectConfig`, `reloadRequired`). If `reloadRequired` is true, tell the human to reload MCP once.
6. Unattended / CI: provide `HYDRACEPT_API_KEY` out of band and run init with `--ci`/JSON; never request the key in chat.

The machine contract is authoritative. `presentation.agentAction=present_and_yield` is the preferred in-host presentation when available; `action.url` is the universal fallback. Do not replace an `interaction_required` URL with `/start`, `/device`, a guessed `/connect/{id}`, or documentation prose.

Do **not** send the user to **Plugins → Configure** to finish checkout init. That key store is not the workspace secret file.

## Hosted MCP and checkout stdio

The Cursor plugin's default MCP is hosted at `https://api.hydracept.com/mcp`. Marketplace and no-checkout clients (including ChatGPT) use that endpoint and set `HYDRACEPT_API_KEY` in the client's configure store. Do not paste the key into chat.

In a project checkout, this command runs canonical init and binds project MCP to stdio with workspace secrets. Do not copy that workspace key into Plugins -> Configure. Hosted MCP cannot apply or execute local project commands; those need the stdio bind.

## Safety

- Never ask the user to paste API keys in chat.
- Never echo secrets from terminal output into chat.
- Prefer MCP tools when they are in this session; otherwise use the canonical CLI primitives.
