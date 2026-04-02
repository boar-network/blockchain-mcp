# Security Policy

## Reporting a Vulnerability

Report security issues through [GitHub Security Advisories](https://github.com/boar-network/blockchain-mcp/security/advisories/new) on this repository. Do not open public issues for security vulnerabilities.

We will acknowledge reports within 72 hours and provide a resolution timeline.

## Scope

Boar blockchain MCP is a **read-only** blockchain data server. By design it:

- **Cannot** send transactions or modify on-chain state
- **Cannot** access private keys, wallets, or signing capabilities
- **Does not** store API keys, credentials, or authentication tokens
- **Does not** collect or retain user data

## Transport Security

- All connections use **HTTPS only** (TLS 1.2+)
- The server is **stateless** — each request is independent with no session data
- No authentication tokens are stored or required
- Hosted on Cloudflare Workers with their platform-level protections
