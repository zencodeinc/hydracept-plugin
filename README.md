# Hydracept — Cursor plugin

Production-ready game assets, with a receipt for every run. Sprite sheets, transparent PNGs, Sheet & Slice, BYOK, through one API.

Hydracept gives game teams production-ready assets through one API. Every job leaves a receipt.

This repository is the Cursor plugin package for Hydracept. It is generated from the
Hydracept monorepo (`public/agents/`) and published here as an
[Agent Plugins 1.0](https://open-plugins.com) package so Cursor can discover it from the
repository root.

## What is in this repository

| Path | Purpose |
|------|---------|
| `plugin.json` | Agent Plugins 1.0 manifest |
| `skills/` | Agent Skills for setup, image generation, sheet slicing, and smoke verification |
| `mcp.json` | Hydracept MCP servers (hosted Streamable HTTP + local stdio fallback) |
| `.cursor-plugin/plugin.json` | Cursor plugin manifest |
| `assets/logo.png` | Plugin logo referenced by the Cursor manifest |

## Install

With the Hydracept CLI:

```bash
python -m hydracept agents install cursor
```

Or add the MCP server directly to a workspace:

```json
{
  "mcpServers": {
    "hydracept": {
      "type": "streamable-http",
      "url": "https://api.hydracept.com/mcp"
    }
  }
}
```

## MCP transports

| Transport | Endpoint |
|-----------|----------|
| Hosted | `https://api.hydracept.com/mcp` |
| Stdio | `python -m hydracept mcp serve` |

Hosted MCP requires `Authorization: Bearer <HYDRACEPT_API_KEY>`. Credentials are supplied by
your client configuration and are never committed to this repository. The stdio server reads
the credential stored by `python -m hydracept login`, which is the recommended path for local
coding agents.

## Skills

- `hydracept`
- `hydracept-setup`
- `hydracept-smoke`
- `hydracept-image`
- `hydracept-sheet`

## Requirements

- Hydracept CLI 0.2.3 or newer for the stdio transport and skill workflows
- A Hydracept API key or workspace login for hosted MCP

## Links

- Product: https://hydracept.com
- Documentation: https://docs.hydracept.com
- OpenAPI: https://hydracept.com/openapi/hydracept-v1.json

## License

Proprietary. See [LICENSE.md](LICENSE.md). Copyright (c) Zencode Consulting Inc.
