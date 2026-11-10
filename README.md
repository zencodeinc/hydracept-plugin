# Hydracept for Cursor

One execution surface for text/reasoning, media, domains, DNS, and other external capabilities, with durable jobs, budgets, receipts, and BYOK.

Plugin homepage: https://hydracept.com/plugin

A Zencode product. Copyright Zencode Consulting Inc.

Hydracept is not in the Cursor Marketplace yet. Install from `https://github.com/zencodeinc/hydracept-plugin` (tag v0.1.10) or run `python -m hydracept agents install --auto`.

The plugin talks to hosted MCP at `https://api.hydracept.com/mcp`. That server starts without Python and without a preinstalled `hydracept` package. When Cursor asks, set `HYDRACEPT_API_KEY` (create one at https://hydracept.com/start). Do not paste the key into chat. Marketplace and no-checkout installs keep using this hosted MCP, with the key stored in Plugins -> Configure.

In a project checkout, `python -m hydracept init --apply --yes --json` stores the key in `.hydracept/secrets.json` and can bind project MCP to stdio. After that, do not also copy the workspace key into **Plugins -> Configure**. Hosted MCP cannot apply or execute local project commands; those need the stdio bind in the project repo.

## What's included

- Hosted MCP at `https://api.hydracept.com/mcp`
- Six skills: `hydracept` (general use), `hydracept-setup` (workspace bootstrap), `hydracept-image` (images and transparent PNGs), `hydracept-sheet` (Sheet and Slice families), `hydracept-inspect` (recover and reuse prior jobs), and `hydracept-smoke` (explicit paid verification)
- Two commands: `/hydracept-init`, `/hydracept-doctor`
- One always-apply rule (`rules/hydracept.mdc`) that keeps API keys out of chat

Logo: `assets/trademark.png` (a 1:1 plated PNG). There is no `assets/logo.png`.

The plugin is MIT licensed and free to install. Paid usage is billed by Hydracept under its own terms.

Terms: https://hydracept.com/terms.html

Privacy: https://hydracept.com/privacy.html

Local CLI fallback (optional): `python -m hydracept agents install --auto`.
