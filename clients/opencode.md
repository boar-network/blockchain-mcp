# Boar blockchain MCP — OpenCode Setup

## Config file location

OpenCode reads `opencode.json` from your project root automatically. You can also add it to the global config at `~/.config/opencode/opencode.json`.

This repo includes a ready-made `opencode.json` at the root — no manual setup needed if you cloned it.

## Basic endpoint (recommended start)

Create or edit `opencode.json` in your project root:

```json
{
  "mcp": {
    "boar-blockchain-mcp-basic": {
      "type": "remote",
      "url": "https://mcp.boar.network/basic"
    }
  }
}
```

## Both endpoints

```json
{
  "mcp": {
    "boar-blockchain-mcp-basic": {
      "type": "remote",
      "url": "https://mcp.boar.network/basic"
    },
    "boar-blockchain-mcp-advanced": {
      "type": "remote",
      "url": "https://mcp.boar.network/advanced"
    }
  }
}
```

OpenCode uses `"type": "remote"` for HTTP MCP servers — no API key or auth headers needed for Boar.

## Global config

To make the servers available in every project, add the same `"mcp"` block to `~/.config/opencode/opencode.json`.

## Verify

1. Run `opencode mcp list` and confirm both servers appear as connected.
2. Start a session and ask: **"What is the ETH balance of vitalik.eth?"**
3. OpenCode should invoke `eth_get_balance` from Boar blockchain MCP.

## Troubleshooting

- **Server not listed** — Ensure `opencode.json` is in the current project root. Run `opencode mcp list` from that directory.
- **Connection error** — Check that `"type": "remote"` is set (not `"local"`). Verify the URL is reachable.
- **Changes not picked up** — OpenCode re-reads config on startup. Restart your session after editing `opencode.json`.
