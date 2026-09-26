# Hydracept for Cursor

Give Cursor's agent image, audio, video, 3D, and text generation, plus domains/DNS and other external capabilities, through one [Hydracept](https://hydracept.com) MCP interface. Every run is a durable job with budgets, typed artifacts, and an immutable receipt. Bring your own provider keys (BYOK) or use managed execution.

- Website: https://hydracept.com
- Plugin page: https://hydracept.com/plugin
- Python package / MCP server: [`hydracept` on PyPI](https://pypi.org/project/hydracept/)
- MCP Registry: `com.hydracept/hydracept`

A Zencode product · © Zencode Consulting Inc.

## What's included

| Component | Name | Purpose |
| --- | --- | --- |
| MCP server | `hydracept` (`mcp.json`) | Stdio MCP: `python -m hydracept mcp serve`. No secrets in the repo. |
| Skills | `hydracept`, `hydracept-setup`, `hydracept-image`, `hydracept-sheet`, `hydracept-smoke` | When and how to use Hydracept capabilities; setup; image generation; sprite/icon sheets; opt-in paid smoke test |
| Commands | `/hydracept-init`, `/hydracept-doctor` | Bootstrap a project; check connection and MCP binding |
| Rule | `hydracept.mdc` | Never ask for API keys in chat; use canonical init and stdio MCP |

## Install

1. Install **Hydracept** from the Cursor Marketplace (Customize → search "Hydracept"), or test locally by copying this repo into `~/.cursor/plugins/local/hydracept` and reloading the window.
2. Install the Python package the MCP server runs on:

   ```bash
   pip install -U hydracept
   ```

## Authentication

Get an account and key at https://hydracept.com/start. Do **not** paste `HYDRACEPT_API_KEY` into chat, and do not put it in **Plugins → Configure** for project checkouts.

In a project checkout, run (or ask the agent to run `/hydracept-init`):

```bash
python -m hydracept init --apply --yes --json
```

Init writes workspace secrets under `.hydracept/` (gitignored) and binds project MCP to stdio. If it returns `status: interaction_required`, open the activation URL from the JSON output, then run the suggested `afterCompletion.command`. Reload MCP once if init says it is required. Run `/hydracept-doctor` to verify.

Other clients:

- **Key-only stdio:** `uvx hydracept mcp serve` with `HYDRACEPT_API_KEY` set in the environment.
- **Hosted MCP (no checkout, e.g. ChatGPT):** `https://api.hydracept.com/mcp` with `Authorization: Bearer <HYDRACEPT_API_KEY>`.

## Example prompts

- "Generate a transparent 512×512 PNG app icon of a paper plane in a flat style and save it to `assets/icon.png`."
- "Make a cohesive set of 8 UI glyphs (home, search, settings, …) as a sprite sheet and slice it into separate PNGs."
- "Create a 10-second upbeat background music loop for the landing page."
- "Generate a short product teaser video from this screenshot."
- "Produce a low-poly 3D model of a coffee cup as a GLB for the three.js scene."
- "Translate `locales/en.json` into French and German as a durable job and show me the receipt."
- "What would it cost to generate 20 hero images? Quote it before running anything."

Available capabilities depend on the live Hydracept catalog; the agent discovers them with `hydracept_capabilities` / `python -m hydracept capabilities find`.

## Pricing

The plugin is free and open source. Hydracept execution is billed by Hydracept: BYOK carries a 0% Hydracept service fee; managed execution is provider price plus 6%. See https://hydracept.com.

## Security

This repository contains no API keys or tokens. Keys stay in `.hydracept/secrets.json` (gitignored) or your environment. Report security issues to support@hydracept.com.

## MCP Registry

Registry manifest: [`mcp-registry/server.json`](./mcp-registry/server.json) (`com.hydracept/hydracept`, version tracks the PyPI package, not this plugin's semver).

## Support

- Email: support@hydracept.com
- Issues: https://github.com/zencodeinc/hydracept-plugin/issues

## License

MIT — see [LICENSE](./LICENSE).
