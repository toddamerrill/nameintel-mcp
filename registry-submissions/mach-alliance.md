# MACH Alliance MCP Registry Submission

**Status:** [ ] not yet submitted
**Submission path:** https://machalliance.org/mach-alliance-mcp-registry (registry submission form). Likely requires a registry account or vendor profile — check current submission flow.
**Owner:** Todd Merrill
**Submission URL:** _fill in after submission_

---

## Vendor / Server profile

**Vendor name:** Silverback CTO
**Server name:** NameIntel
**Category:** Brand & Content Intelligence
**Endpoint:** `https://mcp.nameintel.io/mcp`
**Transport:** Streamable HTTP (per current MCP spec)
**Hosting:** AWS App Runner (us-east-1), CloudFront edge
**Region availability:** Global via CloudFront

**Auth method:** x402 (USDC micropayments). No accounts, no API keys.

**Compliance:**
- TLS 1.2+ enforced
- No PII collected (queries are brand-name strings)
- Caching on first-party DynamoDB with TTLs (domain 30min, trademark 24hr, social 1hr, GEO 7 days)
- Payment settlement via Coinbase x402 facilitator and Solana RPC; receipts on-chain

**SLA:**
- App Runner auto-scaling, target p95 latency < 10s for full score
- Status page: _link when live_
- Changelog: https://api.nameintel.io/changelog.json

## Use cases (enterprise-relevant framing)

- **Brand governance for global enterprises** — score candidate sub-brand, product, or campaign names against trademark/domain/social/GEO risk before legal review.
- **Naming workflow for branding agencies** — replace 4-5 separate tools with a single API call. Agency tier supports white-label and team seats.
- **Agent-mediated business formation** — let autonomous agents perform name validation as part of company-formation pipelines (Stripe Atlas-style flows).

## One-line value proposition for the registry page

> The first agent-native naming tool: five-dimensional brand-name scoring (including AI findability) over MCP, pay-per-call in USDC, MACH-aligned composable.

## Differentiators

- Industry-first GEO (AI findability) score
- x402 native — among the first ~20 MCP servers with production micropayment support
- Composable: tools work standalone or as a five-dimensional pipeline
- Self-describing manifests at `/.well-known/` paths

## Contact

Todd Merrill, CTO — todd@silverbackcto.com
Jim Hasty, GTM — jimh@coglegroup.com
