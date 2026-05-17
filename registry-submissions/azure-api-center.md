# Azure API Center — MCP Catalog Submission

**Status:** [ ] not yet submitted
**Submission path:** Azure API Center MCP catalog. Listing requires either (a) a Microsoft partner / publisher relationship, or (b) the public submission flow documented at learn.microsoft.com/azure/api-center. Verify current path before submitting.
**Owner:** Todd Merrill
**Submission URL:** _fill in after submission_

---

## API definition

**Title:** NameIntel
**Version:** 1.0.0
**Description:** Name intelligence API and MCP server. Score brand names across domain, trademark, social, SEO, and AI findability (GEO). Pay-per-call via x402 micropayments on Base + Solana.
**Type:** REST + MCP (Streamable HTTP)
**OpenAPI spec URL:** https://api.nameintel.io/openapi.json
**MCP manifest URL:** https://api.nameintel.io/.well-known/mcp.json

## Endpoints

- `POST /api/v1/score` — Full 5-dimension score ($0.05 USDC)
- `POST /api/v1/score/basic` — 4 dimensions, no GEO ($0.02)
- `POST /api/v1/check/domain` — Domain availability ($0.01)
- `POST /api/v1/check/trademark` — USPTO trademark conflicts ($0.01)
- `POST /api/v1/check/social` — Handle availability across 12+ platforms ($0.01)
- `POST /api/v1/check/geo` — AI findability score ($0.03)

## Auth

- **Method:** x402 (HTTP 402 Payment Required → sign payload → retry with `X-PAYMENT` header)
- **Chains:** Base (USDC), Solana (USDC)
- **Facilitator:** Coinbase x402 facilitator at `https://x402.coinbase.com/facilitator`
- **No API keys.** No subscriptions. Per-call settlement.

## Categories / tags

`branding`, `naming`, `trademark`, `domain`, `seo`, `ai-findability`, `geo`, `x402`, `mcp`, `micropayments`, `agent-economy`, `business-intelligence`

## Why list in Azure API Center

NameIntel is one of a small set of production MCP servers that combine: (1) remote Streamable HTTP transport, (2) x402 micropayment settlement, (3) machine-readable manifests under `/.well-known/`. This makes it a useful reference for Microsoft enterprise customers exploring agent commerce patterns on Azure.

## Contact

Todd Merrill — todd@silverbackcto.com
