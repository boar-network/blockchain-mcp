# Privacy Policy

## Data Collection

Boar MCP does **not** implement custom logging, user tracking, or telemetry at the application level. Specifically:

- No queries or tool inputs are recorded by Boar MCP
- No responses are cached or retained
- No cookies or client-side tracking of any kind
- No user accounts or authentication

## Infrastructure & Analytics

Boar MCP runs on **Cloudflare Workers**. As part of standard platform operations, Cloudflare collects request metadata including IP addresses, request counts, response times, and error rates. See [Cloudflare's Privacy Policy](https://www.cloudflare.com/privacypolicy/) for details.

We may use Cloudflare's built-in analytics (request volume, geographic distribution, error rates) to monitor service health and guide development decisions. These analytics are aggregate and do not include query content.

## Data Flow

Requests are proxied to blockchain nodes maintained by Boar and returned directly to the caller. The server is stateless — it does not cache, store, or retain any request or response data at the application level.

All blockchain data involved in queries (addresses, transaction hashes, block numbers) is already public information on the respective blockchains.

## Third-Party Services

| Service | Role | Their Privacy Policy |
|---------|------|---------------------|
| [Cloudflare Workers](https://www.cloudflare.com/privacypolicy/) | Hosting & analytics | Collects standard HTTP request metadata as part of platform operations |
| Blockchain nodes maintained by Boar | Data source | Receive the blockchain queries necessary to fulfill requests |
| [4byte.directory](https://www.4byte.directory/) | Function selector lookups | Receives function selectors for signature resolution |
| [Sourcify](https://sourcify.dev/) | ABI verification | Receives contract addresses for verified ABI retrieval |

## Data Sharing

No user data is shared beyond the blockchain queries themselves and the standard request metadata visible to Cloudflare as the hosting provider. The server acts as a stateless proxy — it forwards blockchain data requests and returns the results.
