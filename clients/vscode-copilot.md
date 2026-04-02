# Boar blockchain MCP — VS Code GitHub Copilot Setup

## Config file location

Create or edit `.vscode/mcp.json` in your workspace root.

## Basic endpoint (recommended start)

```json
{
  "servers": {
    "boar-blockchain-mcp-basic": {
      "type": "http",
      "url": "https://mcp.boar.network/basic"
    }
  }
}
```

## Both endpoints

```json
{
  "servers": {
    "boar-blockchain-mcp-basic": {
      "type": "http",
      "url": "https://mcp.boar.network/basic"
    },
    "boar-blockchain-mcp-advanced": {
      "type": "http",
      "url": "https://mcp.boar.network/advanced"
    }
  }
}
```

## Verify

1. Open the **Copilot Chat** panel (Ctrl+Shift+I / Cmd+Shift+I).
2. Switch to **Agent** mode using the mode selector at the top of the chat.
3. Ask: **"What is the ETH balance of vitalik.eth?"**
4. Copilot should discover and invoke the `eth_get_balance` tool.

## Troubleshooting

- **Tools not showing up** — MCP support requires VS Code 1.99+ and GitHub Copilot extension. Make sure both are up to date.
- **"No tools available" in chat** — Ensure you're in Agent mode, not Ask or Edit mode. MCP tools only appear in Agent mode.
- **Config not detected** — The file must be at `.vscode/mcp.json` (not inside `settings.json`). Reload the VS Code window after creating it.
