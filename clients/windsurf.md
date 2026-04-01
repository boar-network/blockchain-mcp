# Boar MCP — Windsurf Setup

## Config file location

Edit `~/.codeium/windsurf/mcp_config.json` (create the file if it doesn't exist).

## Basic endpoint (recommended start)

```json
{
  "mcpServers": {
    "boar-mcp-basic": {
      "serverUrl": "https://mcp.boar.network/basic"
    }
  }
}
```

## Both endpoints

```json
{
  "mcpServers": {
    "boar-mcp-basic": {
      "serverUrl": "https://mcp.boar.network/basic"
    },
    "boar-mcp-advanced": {
      "serverUrl": "https://mcp.boar.network/advanced"
    }
  }
}
```

## Verify

1. Restart Windsurf after editing the config.
2. Open **Cascade** and check that the MCP tools icon shows available tools.
3. Ask: **"What is the ETH balance of vitalik.eth?"**

## Troubleshooting

- **Tools not appearing after restart** — Double-check the file path. On macOS/Linux it's `~/.codeium/windsurf/mcp_config.json`. On Windows it's `%USERPROFILE%\.codeium\windsurf\mcp_config.json`.
- **Server shows as disconnected** — Validate your JSON syntax. A trailing comma or missing brace will silently fail.
- **Cascade doesn't use tools** — Make sure you're using a model that supports tool use in Cascade.
