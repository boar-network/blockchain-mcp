# Boar MCP — Gemini CLI Setup

## Add via CLI

### Basic endpoint (recommended start)

```sh
gemini mcp add --transport http boar-mcp-basic https://mcp.boar.network/basic
```

### Advanced endpoint

```sh
gemini mcp add --transport http boar-mcp-advanced https://mcp.boar.network/advanced
```

## Or add via config file

Edit `~/.gemini/settings.json` (create it if it doesn't exist):

```json
{
  "mcpServers": {
    "boar-mcp-basic": {
      "httpUrl": "https://mcp.boar.network/basic"
    },
    "boar-mcp-advanced": {
      "httpUrl": "https://mcp.boar.network/advanced"
    }
  }
}
```

## Verify

1. Start the Gemini CLI: `gemini`
2. Ask: **"What is the ETH balance of vitalik.eth?"**
3. Gemini should discover and call the `eth_get_balance` tool.

## Troubleshooting

- **"Unknown transport type" error** — Update Gemini CLI to the latest version.
- **Tools not discovered** — Run `gemini mcp list` to check if the servers are registered. Re-add if needed.
- **Connection errors** — Verify that `https://mcp.boar.network/basic` is reachable from your network.
