# Changelog

## Unreleased

- Add `mcp-registry/server.json` for the official MCP Registry (`com.hydracept/hydracept`, PyPI stdio + hosted remote)
- Add `.cursor-plugin/marketplace.json`; point `plugin.json` repository at this repo
- README: canonical repo note, install/auth, and registry publishing guidance

## 0.1.8

- Stdio MCP (`python -m hydracept mcp serve`) using CLI workspace secrets; no secrets in git
- Skills, commands, and a rule that never solicits API keys in chat
- Cursor Marketplace schema: plugin.json + `.cursor-plugin/marketplace.json`
