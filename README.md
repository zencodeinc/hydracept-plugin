# Hydracept for Cursor

One execution surface for text/reasoning, media, domains, DNS, and other external capabilities, with durable jobs, budgets, receipts, and BYOK.

Plugin homepage: https://hydracept.com/plugin

A Zencode product · © Zencode Consulting Inc.

Hydracept is not in the Cursor Marketplace yet. Install from `https://github.com/zencodeinc/hydracept-plugin` (tag v0.1.10) or run `python -m hydracept agents install --auto`.

The plugin talks to hosted MCP at `https://api.hydracept.com/mcp`. That server starts without Python and without a preinstalled `hydracept` package. When Cursor asks, set `HYDRACEPT_API_KEY` (create one at https://hydracept.com/start). Do not paste the key into chat.

In a project checkout, `python -m hydracept init --apply --yes --json` stores the key in `.hydracept/secrets.json` and binds project MCP to stdio. After that, do not also copy the workspace key into **Plugins → Configure**.

Commands: `/hydracept-init`, `/hydracept-doctor`.

Terms: https://hydracept.com/terms.html

Privacy: https://hydracept.com/privacy.html

Local CLI fallback (optional): `python -m hydracept agents install --auto`.
