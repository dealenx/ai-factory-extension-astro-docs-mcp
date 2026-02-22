# ai-factory-extension-astro-docs-mcp

An [ai-factory](https://github.com/lee-to/ai-factory) extension that adds the [Astro Docs MCP server](https://docs.astro.build) to all your AI agents. Once installed, agents (Claude Code, Cline, etc.) can query the official Astro documentation directly through MCP.

## Quick Start

```bash
# from a local directory
ai-factory extension add ./ai-factory-extension-astro-docs-mcp

# or from a git repo
ai-factory extension add https://github.com/<user>/ai-factory-extension-astro-docs-mcp.git
```

That's it — ai-factory merges the Astro Docs MCP server config into every agent that supports MCP.

## Project Structure

```
ai-factory-extension-astro-docs-mcp/
├── extension.json       # Extension manifest
├── mcp/
│   └── astro-docs.json  # Astro Docs MCP server config
├── package.json
├── LICENSE
└── README.md
```

## How It Works

### extension.json

The manifest declares the Astro Docs MCP server:

```json
{
  "name": "ai-factory-extension-astro-docs-mcp",
  "version": "1.0.0",
  "description": "Astro Docs MCP server as an ai-factory extension",
  "mcpServers": [
    {
      "key": "astro-docs",
      "template": "./mcp/astro-docs.json",
      "instruction": "Astro Docs MCP: provides access to the official Astro documentation"
    }
  ]
}
```

### MCP Template (`mcp/astro-docs.json`)

The server connects to the remote Astro Docs MCP endpoint via `mcp-remote`:

```json
{
  "command": "npx",
  "args": ["-y", "mcp-remote", "https://mcp.docs.astro.build/mcp"]
}
```

No API keys or additional configuration required.

## Managing the Extension

```bash
# List installed extensions
ai-factory extension list

# Remove the extension
ai-factory extension remove ai-factory-extension-astro-docs-mcp
```

## Documentation

- [ai-factory Extensions Guide](https://github.com/lee-to/ai-factory/blob/2.x/docs/extensions.md) — full reference for extension manifest fields, MCP servers, injections, commands, skills, and agents.
- [Astro Docs MCP](https://docs.astro.build) — official Astro documentation.

## License

[MIT](LICENSE)
