# Changelog

## Unreleased

## 0.1.9

- Claude Code plugin (`.claude-plugin/`) with hosted MCP `https://api.hydracept.com/mcp` and API key via plugin configure
- Gemini CLI extension (`gemini-extension.json`)
- README install sections for Claude Code, Claude Desktop, Google Antigravity, and Gemini CLI
- CI: validate Claude Code and Gemini CLI manifests on pull requests

## 0.1.8

- Marketplace listing polish: clearer description and keywords (image/audio/video/3D/text), drop game-only tags
- README: what's included, install, auth, example prompts, pricing, support
- `hydracept-image` skill: general-purpose image wording
- Add `mcp-registry/server.json` for the official MCP Registry (`com.hydracept/hydracept`, PyPI stdio + hosted remote)
- Add `.cursor-plugin/marketplace.json`; point `plugin.json` repository at this repo
- README: canonical repo note, install/auth, and registry publishing guidance
- Stdio MCP (`python -m hydracept mcp serve`) using CLI workspace secrets; no secrets in git
- Skills, commands, and a rule that never solicits API keys in chat
- Cursor Marketplace schema: plugin.json + `.cursor-plugin/marketplace.json`
