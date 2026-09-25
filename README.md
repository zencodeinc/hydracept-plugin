# Hydracept for Cursor

One execution surface for text/reasoning, media, domains, DNS, and other external capabilities, with durable jobs, budgets, receipts, and BYOK.

**Canonical repository:** [`zencodeinc/hydracept-plugin`](https://github.com/zencodeinc/hydracept-plugin) (Cursor plugin **0.1.8**). The older [`zencodeinc/hydracept-agent-plugins`](https://github.com/zencodeinc/hydracept-agent-plugins) catalog is retired.

Plugin homepage: https://hydracept.com/plugin

A Zencode product · © Zencode Consulting Inc.

## Install

- **Cursor Marketplace:** search for **Hydracept** or submit this repo at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish) after review.
- **From Git:** clone `https://github.com/zencodeinc/hydracept-plugin` and add the repo as a Cursor plugin (root contains `.cursor-plugin/plugin.json`).

Requires the [`hydracept`](https://pypi.org/project/hydracept/) Python package on your machine for stdio MCP (`python -m hydracept …`).

## Authentication (project checkout)

Do **not** paste `HYDRACEPT_API_KEY` into chat or into **Plugins → Configure** for workspace-bound stdio.

In a project checkout run:

```bash
python -m hydracept init --apply --yes --json
```

That writes workspace secrets under `.hydracept/` and binds project MCP to stdio (`python -m hydracept mcp serve`). Reload MCP once when init says it is required.

If init returns `status: interaction_required`, follow the Hydracept activation URL from the JSON output, then run the suggested `afterCompletion.command` (usually the same init with `--wait`).

**Hosted MCP (no checkout):** `https://api.hydracept.com/mcp` with `Authorization: Bearer <HYDRACEPT_API_KEY>`. Get a key at https://hydracept.com/start .

**Quick key-only stdio:** `uvx hydracept@0.4.4 mcp serve` with `HYDRACEPT_API_KEY` set (see [MCP Registry manifest](./mcp-registry/server.json)).

Commands: `/hydracept-init`, `/hydracept-doctor`.

Local CLI fallback (optional): `python -m hydracept agents install --auto`.

## MCP Registry

Official registry manifest: [`mcp-registry/server.json`](./mcp-registry/server.json).

- **Registry name (domain namespace):** `com.hydracept/hydracept` — aligned with the PyPI README `mcp-name` line in the `zencodeinc/hydracept` monorepo (owner verifies **hydracept.com** for the `com.hydracept` namespace).
- **Manifest version `0.4.4`** tracks the published PyPI MCP server, not the Cursor plugin semver (`0.1.8`).

Publishing is manual: validate with `mcp-publisher validate mcp-registry/server.json`, then `cd mcp-registry && mcp-publisher publish` after domain verification and PyPI README ownership are complete. Do not publish the hosted remote until redirect/TLS issues on `https://api.hydracept.com/mcp` are fixed.

## License

MIT — see [LICENSE](./LICENSE).
