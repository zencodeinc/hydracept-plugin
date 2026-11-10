# Changelog

## Unreleased

- Docs: correct the 0.1.10 changelog, README, image skill, and MCP path copy for Cursor Marketplace review. The plugin is a single-plugin repo, so `.cursor-plugin/marketplace.json` is omitted. The plugin MCP is hosted at `https://api.hydracept.com/mcp`. The image skill uses general wording, not game-only wording. README lists all six skills and the API-key rule. Replace remaining em dashes in skills and commands.

## 0.1.10

- Hosted MCP so the plugin starts without local Python or a preinstalled package
- Skills, commands, and a rule that never solicits API keys in chat
- Cursor Marketplace schema: single-plugin layout with `.cursor-plugin/plugin.json` at the repo root. `.cursor-plugin/marketplace.json` was removed because the official Cursor plugin template says single-plugin repos should omit it.
