# Boar MCP — Cursor Setup

## Config file location

Create or edit `.cursor/mcp.json` in your project root.

## Basic endpoint (recommended start)

```json
{
  "mcpServers": {
    "boar-mcp-basic": {
      "url": "https://mcp.boar.network/basic"
    }
  }
}
```

## Both endpoints

```json
{
  "mcpServers": {
    "boar-mcp-basic": {
      "url": "https://mcp.boar.network/basic"
    },
    "boar-mcp-advanced": {
      "url": "https://mcp.boar.network/advanced"
    }
  }
}
```

Cursor supports streamable-http natively — no transport type field needed.

## Verify

1. Open **Cursor Settings > MCP** and confirm the servers show a green status indicator.
2. Open **Composer** (Cmd+I / Ctrl+I) and ask: **"What is the ETH balance of vitalik.eth?"**
3. The agent should use the `eth_get_balance` tool from Boar MCP.

## Troubleshooting

- **Server shows red/disconnected** — Verify the JSON syntax in `.cursor/mcp.json`. Restart Cursor after editing.
- **Tools not available in Composer** — MCP tools only work in Agent mode. Make sure you're using Composer with an agent-capable model.
- **Changes not picked up** — Cursor may cache MCP config. Fully restart the application after editing `.cursor/mcp.json`.
