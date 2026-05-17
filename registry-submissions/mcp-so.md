# MCP.so Submission

**Status:** [ ] not yet submitted
**Submission path:** https://mcp.so/submit (web form) or PR to https://github.com/chatmcp/mcp-directory
**Owner:** Todd Merrill
**PR / submission URL:** _fill in after submission_

---

## Form fields

**Name:** NameIntel

**Category:** Business / Branding / Marketing

**Description (short, ~140 chars):**
> Score brand names across domain, trademark, social, SEO, and AI findability. Pay-per-call via x402 — no signup, no API keys.

**Description (long):**
> NameIntel is a remote MCP server that scores brand names across five dimensions: domain availability, USPTO trademark conflict risk, social handle availability across 12+ platforms, SEO keyword strength, and AI findability (the GEO score — industry-first). One MCP endpoint, five tools, $0.01–$0.05 per call paid in USDC over the x402 protocol on Base or Solana. No accounts, no API keys, no rate-limit setup — payment IS authentication.
>
> Built for the agent economy: when an AI agent helps a founder start a company, the first thing it needs is a clear-to-launch brand name. NameIntel is the tool that agent calls.

**Server URL:** `https://mcp.nameintel.io/mcp`

**Transport:** Streamable HTTP

**Auth:** x402 (USDC micropayments on Base + Solana)

**Tools:**
- `score_name` — 5-dimensional composite score with sub-scores and verdict ($0.05)
- `check_domain` — domain availability + pricing across TLDs ($0.01)
- `check_trademark` — USPTO trademark conflict screening ($0.01)
- `check_social` — handle availability across 12+ platforms ($0.01)
- `check_geo` — AI findability score (ChatGPT/Perplexity/Claude/Gemini) ($0.03)

**Install command:**
```
claude mcp add --transport http nameintel https://mcp.nameintel.io/mcp
```

**Homepage:** https://nameintel.io
**Docs:** https://nameintel.io/api
**MCP manifest:** https://api.nameintel.io/.well-known/mcp.json
**Repo:** _set when public_
**License:** Proprietary (commercial)
**Author:** Silverback CTO

**Tags:** branding, naming, trademark, domain, seo, geo, x402, micropayments, agent-economy
