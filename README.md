# SpecMCP

**SpecMCP gives AI assistants live access to gematik's Telematikinfrastruktur (TI) specifications and certification requirements.**

SpecMCP is a hosted, remote [Model Context Protocol (MCP)](https://modelcontextprotocol.io) server. Instead of relying on stale training data, your AI client queries a continuously updated database of TI specifications (the `gemSpec_*` document set), requirements (AFOs such as `A_12345` / `GS-A_4101`), and certification scopes (`gemProdT` / `gemAnbT`) — and can diff exactly what changed between versions.

Built for the teams that build and certify TI products: manufacturers, Zulassung specialists, and compliance and product engineers who need answers that match the current normative documents.

- **Website:** https://specmcp.com
- **Docs:** https://docs.specmcp.com
- **Server URL:** `https://mcp.specmcp.com/mcp`

> This repository is the public home for the hosted SpecMCP server. SpecMCP is a hosted service; the server source is not distributed here.

This repo is also a conformant [Agent Plugin](https://agent-plugins.org): `plugin.json` and `mcp.json` declare the hosted Streamable HTTP server so compatible clients (Cursor, and others implementing the standard) can discover and install it. Authentication is OAuth 2.0, handled per-user by the client; no credentials are stored in the package.

## Connect

SpecMCP is a remote MCP server secured with OAuth 2.0. You need a [SpecMCP account](https://app.specmcp.com) and an active plan. On first connect, your client runs the OAuth sign-in automatically.

Per-client guides:

- **Claude:** https://docs.specmcp.com/docs/connect/claude
- **ChatGPT:** https://docs.specmcp.com/docs/connect/chatgpt
- **Cursor:** https://docs.specmcp.com/docs/connect/cursor
- **Others (Codex, Copilot, …):** https://docs.specmcp.com/docs/connect/other

Example (Claude Code):

```bash
claude mcp add --transport http specmcp https://mcp.specmcp.com/mcp
```

## Tools

All tools are read-only; SpecMCP retrieves and compares specifications and never modifies your data.

| Tool | Purpose |
|------|---------|
| `list_specs` | Browse all available TI specifications |
| `search_requirements` | Semantic search across requirements |
| `get_requirement` / `get_requirements` | Fetch full requirement text by ID (single or batch) |
| `list_requirements` | All requirements for a spec |
| `list_scopes` | Certification scopes (gemProdT / gemAnbT) |
| `list_scope_specs` | Specs covered by a scope |
| `list_scope_requirements` | The full certification checklist for a scope |
| `diff_versions` | Changes between two spec versions |
| `diff_scope_versions` | Changes between two certification versions |
| `get_spec_version_history` | Version history for a spec |

Full tool reference: https://docs.specmcp.com/docs/troubleshooting-reference/mcp-tools

## Security

To report a security vulnerability, email security@specmcp.com. Please do not open a public issue for security reports. We aim to acknowledge reports within two business days.

## Legal

- **Privacy:** https://specmcp.com/privacy
- **Terms:** https://specmcp.com/terms
- **Imprint:** https://specmcp.com/imprint

SpecMCP is an independent product and is not affiliated with, endorsed by, or sponsored by gematik GmbH. Names such as "gematik" and "Telematikinfrastruktur" are used only to describe the publicly published specifications SpecMCP provides access to.
