# x402.org Showcase Submission

**Status:** [ ] not yet submitted
**Submission path:** https://x402.org (showcase submission form) or PR to https://github.com/coinbase/x402 (look for `apps/` or `showcase/` directory at submission time)
**Owner:** Todd Merrill
**Submission URL:** _fill in after submission_

---

## Application profile

**Name:** NameIntel
**Category:** AI / Agents / API
**Chains:** Base (primary), Solana (secondary)
**Asset:** USDC

**Tagline:** First naming tool in the agent economy — pay $0.01 to $0.05 USDC per call, no signup required.

**Description:**
> NameIntel is a name intelligence API and MCP server that uses x402 as its only authentication mechanism. There are no API keys, no signups, and no subscriptions — every call to one of NameIntel's seven endpoints returns HTTP 402 with a price menu, the agent signs a USDC payment payload, retries with `X-PAYMENT`, and the Coinbase facilitator verifies and settles.
>
> Built specifically to demonstrate that x402 makes a category of API economically viable that Stripe cannot: per-call pricing below $0.50 net of fees. A $0.01 trademark check or $0.05 brand-name score can't profitably exist on card rails.

## Endpoints with USDC pricing

| Endpoint | Price (USDC) | What it does |
|---|---|---|
| `POST /api/v1/score` | 0.05 | Full 5-dimensional brand-name score |
| `POST /api/v1/score/basic` | 0.02 | 4 dimensions, no GEO |
| `POST /api/v1/check/domain` | 0.01 | Domain availability across TLDs |
| `POST /api/v1/check/trademark` | 0.01 | USPTO trademark conflict screen |
| `POST /api/v1/check/social` | 0.01 | Handle availability, 12+ platforms |
| `POST /api/v1/check/geo` | 0.03 | AI findability score (industry-first) |

## Live links

- **Site:** https://nameintel.io
- **API:** https://api.nameintel.io
- **x402 manifest:** https://api.nameintel.io/.well-known/x402
- **MCP server:** https://mcp.nameintel.io/mcp
- **OpenAPI:** https://api.nameintel.io/openapi.json
- **Facilitator:** https://x402.coinbase.com/facilitator (Base)

## Why this is a good showcase

- Production traffic from real MCP clients (Claude Desktop, Claude Code) — not a demo.
- Seven priced endpoints all behind x402. Easy to read the catalog and price tiering.
- Self-describing manifests at `/.well-known/x402` and via the 402 response itself (returns the menu, not just the bill).
- Co-authored case study available if Coinbase developer relations wants one.

## Contact

Todd Merrill — todd@silverbackcto.com
