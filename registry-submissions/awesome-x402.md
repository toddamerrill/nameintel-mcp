# awesome-x402 Submission

**Status:** [ ] not yet submitted
**Submission path:** PR to https://github.com/coinbase/x402 (or the community fork that hosts `awesome-x402`). Check the README at submission time for canonical location.
**Owner:** Todd Merrill
**PR URL:** _fill in after submission_

---

## PR title
> Add NameIntel — brand-name intelligence API + MCP server with x402 settlement

## Markdown entry to add

```markdown
- **[NameIntel](https://nameintel.io)** — Name intelligence API and MCP server. Scores brand names across domain, trademark, social, SEO, and AI findability (GEO). $0.01–$0.05 USDC per call on Base + Solana. No signup, no API keys — payment IS authentication. MCP endpoint: `https://mcp.nameintel.io/mcp`. Manifest: [/.well-known/x402](https://api.nameintel.io/.well-known/x402).
```

## Section
**Applications** or **MCP Servers using x402** (whichever section is canonical at submission time). If both exist, list under both with a brief reason.

## PR description body

```
Adds NameIntel — a name intelligence service that uses x402 as its only auth mechanism. Notable for this list:

- Production endpoints, not a demo. Seven priced endpoints from $0.01 to $0.05 USDC.
- Dual-rail: Base + Solana, with the Coinbase facilitator on Base.
- Self-describing: the 402 response returns the price menu (every endpoint + cheaper alternatives), and `/.well-known/x402` carries the full payment manifest.
- Pairs an x402 REST API with a remote MCP server, so the same scoring engine is reachable from both classic HTTP integrations and Claude Desktop/Code clients.

Happy to add an architecture writeup or be a customer case study if useful.
```
