# Anthropic AAIF Registry Submission

**Status:** [ ] not yet submitted (registry being implemented per Dec 2025 donation announcement)
**Submission path:** Anthropic Agentic AI Foundation Registry. Check Anthropic developer docs or AAIF GitHub for canonical submission flow as it goes live.
**Owner:** Todd Merrill
**Submission URL:** _fill in after submission_

---

## Why this one matters

AAIF is being positioned as the official standard registry. Being in the first cohort when it ships is disproportionately valuable for both visibility and credibility.

## Submission profile

**Name:** NameIntel
**Type:** Remote MCP server (Streamable HTTP)
**Endpoint:** `https://mcp.nameintel.io/mcp`
**Publisher:** Silverback CTO (Todd Merrill, Jim Hasty)
**License:** Proprietary (commercial)

**Description:**
> Name intelligence MCP server. Scores brand names across domain availability, USPTO trademark risk, social handle availability across 12+ platforms, SEO keyword strength, and AI findability (GEO score). Pay-per-call via x402 micropayments on Base + Solana — no API keys, no signup, no rate-limit setup.

**Tools (with prices):**
- `score_name` — $0.05 USDC
- `check_domain` — $0.01 USDC
- `check_trademark` — $0.01 USDC
- `check_social` — $0.01 USDC
- `check_geo` — $0.03 USDC

**Manifests:**
- `/.well-known/mcp.json` — https://api.nameintel.io/.well-known/mcp.json
- `/.well-known/x402` — https://api.nameintel.io/.well-known/x402
- OpenAPI 3.1 — https://api.nameintel.io/openapi.json
- Changelog — https://api.nameintel.io/changelog.json

## Differentiators worth flagging to AAIF maintainers

- Among the earliest production MCP servers using x402 micropayments.
- Industry-first GEO (AI findability) measure.
- Reference implementation of a "Velocity Discoverability Spec" — well-known files, OpenAPI, changelog, and menu-style 402 responses all wired up before launch.

## Contact

Todd Merrill — todd@silverbackcto.com

## Watch list

- AAIF schema spec (may require manifest fields we don't yet expose — track and add)
- AAIF authentication conventions for paid services (we should be the reference for x402 if/when they accept it)
