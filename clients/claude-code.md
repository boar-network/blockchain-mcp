# Boar MCP — Claude Code Setup

## Add via CLI

### Basic endpoint (recommended start)

```sh
claude mcp add boar-mcp-basic --transport http --scope project https://mcp.boar.network/basic
```

### Advanced endpoint

```sh
claude mcp add boar-mcp-advanced --transport http --scope project https://mcp.boar.network/advanced
```

### Verify

```sh
claude mcp list
```

You should see `boar-mcp-basic` and/or `boar-mcp-advanced` in the output.

## Add via project config

Create or edit `.mcp.json` in your project root:

```json
{
  "mcpServers": {
    "boar-mcp-basic": {
      "type": "http",
      "url": "https://mcp.boar.network/basic"
    },
    "boar-mcp-advanced": {
      "type": "http",
      "url": "https://mcp.boar.network/advanced"
    }
  }
}
```

This file can be checked into version control so your whole team gets the same MCP setup.

## Verify

1. Run `claude mcp list` to confirm the servers are registered.
2. Start a conversation and ask: **"What is the ETH balance of vitalik.eth?"**
3. Claude Code should invoke the `eth_get_balance` tool automatically.

## Troubleshooting

- **Server not showing in `mcp list`** — Re-run the `claude mcp add` command. Make sure you spelled the transport type correctly (`http`).
- **"Transport not supported" error** — Update Claude Code to the latest version.
- **Tools not being invoked** — Make sure you approve the MCP tools when prompted. Check that the server appears as "connected" in the list.
