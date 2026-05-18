# MACH Alliance MCP Registry — Ready-to-paste Submission

**Form URL:** https://form.typeform.com/to/S35H6Wa0
**Membership required:** No (open submission per the FAQ)
**Estimated time to fill:** 5–8 minutes

Open the form in a browser, then paste the answers below as you go. Order may vary; the Typeform is dynamic, but every field is covered.

---

## Server identity

- **Server name:** `NameIntel`
- **MCP server ID:** `io.nameintel/server`
- **One-line summary:** First agent-native naming intelligence service. Scores brand names across five dimensions including AI findability; pay-per-call via x402.
- **Vendor / publisher:** Silverback CTO
- **Website:** https://nameintel.io
- **Public repo:** https://github.com/toddamerrill/nameintel-mcp
- **License:** MIT (public mirror) · commercial pay-per-call for the hosted service

## Server endpoint

- **Endpoint URL:** `https://mcp.nameintel.io/mcp`
- **Transport:** Streamable HTTP (current MCP spec)
- **Deployment region:** us-east-1 · global via CloudFront
- **Hosting platform:** AWS App Runner behind CloudFront

## Auth & payment

- **Authentication method:** x402 micropayment protocol — payment is authentication. No accounts, no API keys.
- **Settlement chains:** Base (primary), Solana (planned)
- **Settlement asset:** USDC
- **Facilitator:** https://api.cdp.coinbase.com/platform/v2/x402

## Capabilities

- **Tool count:** 5
- **Tools (names + one-line descriptions):**
  - `score_name` — score a brand name across all five dimensions
  - `check_domain` — domain availability + pricing across TLDs
  - `check_trademark` — USPTO trademark conflict screen
  - `check_social` — handle availability across 12+ platforms
  - `check_geo` — AI findability score (industry-first)

## Category

- **Primary:** Brand & Content Intelligence (or "Marketing / Brand" if their taxonomy uses that label)
- **Tags:** branding, naming, trademark, domain, seo, geo, ai-findability, agent-economy, x402, micropayments, mcp

## Documentation

- **OpenAPI 3.1 spec:** https://api.nameintel.io/openapi.json
- **MCP manifest:** https://api.nameintel.io/.well-known/mcp.json
- **x402 payment manifest:** https://api.nameintel.io/.well-known/x402
- **Health / capability inventory:** https://api.nameintel.io/health
- **Changelog:** https://api.nameintel.io/changelog.json

## Compliance / security

- **TLS:** 1.2+ enforced via CloudFront
- **PII collection:** None. Queries are brand-name strings only.
- **Data residency:** us-east-1 (AWS)
- **Auth model:** Stateless. Every request is independently paid + verified; no session storage.
- **Caching:** First-party DynamoDB with per-dimension TTLs (domain 30min, trademark 24hr, social 1hr, GEO 7 days). No third-party data sharing.

## SLA

- **Architecture:** AWS App Runner auto-scaling
- **Target p95 latency:** < 10s for full 5-dimension score
- **Status page:** https://api.nameintel.io/health (programmatic), human-readable status page coming Phase 2
- **Versioning:** semver via /changelog.json; published as `io.nameintel/server` v1.0.0

## Value proposition (use as the long-form pitch field)

> NameIntel is one of the earliest production MCP servers using x402 micropayments. It's also the only naming-intelligence tool that measures AI findability — the GEO score — which becomes the load-bearing dimension of naming as AI-generated answers increasingly decide which brands consumers ever hear of. We ship as a remote Streamable HTTP server (zero-install) with a self-describing 402 response that returns the price menu on every miss, making it suitable for autonomous agent workflows that need to discover, price, and call services without a human in the loop. Registered in the official MCP Registry as `io.nameintel/server`.

## Contacts

- **Primary technical:** Todd Merrill — todd@silverbackcto.com
- **Primary business:** Jim Hasty — jimh@coglegroup.com
- **General:** todd@silverbackcto.com
