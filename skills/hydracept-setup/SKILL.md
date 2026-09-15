---
name: hydracept-setup
description: Bootstrap Hydracept in a coding agent workspace - check for the CLI, authenticate the project, and connect MCP. Use when Hydracept is not configured yet, when python -m hydracept init must run, when init returns interaction_required and the human must open a connect URL, or when setting up Hydracept unattended in CI with HYDRACEPT_API_KEY.
license: Proprietary
---

# Hydracept Setup

Marketplace-first bootstrap for Hydracept in a coding agent workspace.

## Flow

1. Check whether the Hydracept CLI is installed: `python -m hydracept --help`
2. If missing, explain the install path and ask for approval before running any install command
3. Verify version is at least the plugin `minimumHydraceptVersion`
4. Run `python -m hydracept init --apply --yes --json`
5. If status is `interaction_required`:
   - Present `action.url` to the human
   - If they use multiple GitHub or Google accounts, tell them to pick the correct account on the connect page
   - After they confirm browser setup, run `python -m hydracept init --apply --yes --json --wait`
6. Unattended / CI: set `HYDRACEPT_API_KEY` and use `init --apply --yes --json` or `--ci`
7. Offer `/hydracept-smoke` after MCP is available
8. For project surfaces: in the game repo, use stdio MCP `hydracept_project_up_install` or `python -m hydracept project up --install`. Hosted MCP cannot apply or execute local argv. Do not leave the watcher in a Cursor background terminal.

## Safety

- Never solicit credentials in conversation
- Never echo secrets from terminal output into chat
- Do not inspect provider credential values in `.env` files — let `init` handle discovery
