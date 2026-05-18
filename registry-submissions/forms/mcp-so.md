# MCP.so — Ready-to-paste Submission

**Form URL:** https://mcp.so/submit (may require sign-in with GitHub)
**Alternative:** PR to https://github.com/chatmcp/mcp-directory if the web form isn't your fit (their backing data is in `data/install.sql`; a contributor PR with a new row would work for a senior maintainer review)
**Estimated time:** 5–7 minutes
**Recipient:** mcp.so directory team

mcp.so blocks automated traffic, so this needs to be a manual browser submission. Fill the form using the values below.

---

## Basic info

- **Name:** NameIntel
- **Slug:** nameintel-mcp (or `io-nameintel-server` if they want the registry-style ID)
- **Tagline / short description (≤ 140 chars):**
  > Score brand names across domain, trademark, social, SEO, and AI findability (GEO). Pay-per-call via x402 — no signup, no API keys.

- **Full description:**
  > NameIntel is a remote MCP server that scores brand names across five dimensions in a single call: domain availability, USPTO trademark conflict screening, social handle availability across 12+ platforms, SEO keyword strength, and AI findability (GEO score — industry-first; measures how findable a name is in ChatGPT, Perplexity, Claude, and Gemini answers).
  >
  > Pricing is $0.01–$0.05 per call in USDC over the x402 micropayment protocol on Base and Solana. There are no API keys to provision, no accounts to register, and no rate-limit forms to fill out. Payment is authentication.
  >
  > Built for the AI agent economy: when an autonomous agent helps a founder start a company, NameIntel is the tool that agent calls. Registered in the official MCP Registry as `io.nameintel/server`.

## Endpoint / install

- **Type:** Remote (no install required)
- **Transport:** Streamable HTTP
- **Server URL:** `https://mcp.nameintel.io/mcp`
- **Install command (Claude Code):**
  ```
  claude mcp add --transport http nameintel https://mcp.nameintel.io/mcp
  ```
- **Claude Desktop:** Settings → Connectors → paste the URL

## Identity

- **Author / publisher:** Silverback CTO
- **Author URL:** https://silverbackcto.com
- **Contact email:** todd@silverbackcto.com
- **Public repo:** https://github.com/toddamerrill/nameintel-mcp
- **License:** MIT (public mirror); commercial pay-per-call for the hosted service

## Discovery / docs

- **Homepage:** https://nameintel.io
- **MCP manifest:** https://api.nameintel.io/.well-known/mcp.json
- **OpenAPI 3.1:** https://api.nameintel.io/openapi.json
- **x402 payment manifest:** https://api.nameintel.io/.well-known/x402
- **Changelog:** https://api.nameintel.io/changelog.json

## Tools (5)

| Name | Description | Price |
|---|---|---|
| `score_name` | 5-dimensional composite score | $0.05 USDC |
| `check_domain` | Domain availability across TLDs | $0.01 USDC |
| `check_trademark` | USPTO trademark conflict screen | $0.01 USDC |
| `check_social` | Handle availability, 12+ platforms | $0.01 USDC |
| `check_geo` | AI findability score (industry-first) | $0.03 USDC |

## Category / tags

- **Primary category:** Business / Branding / Marketing
- **Tags:** `branding`, `naming`, `trademark`, `domain`, `seo`, `geo`, `ai-findability`, `x402`, `micropayments`, `agent-economy`, `mcp`, `streamable-http`

## Auth model

- **Type:** x402 (pay-per-call via USDC on Base + Solana)
- **Free tier:** None — but a single call costs $0.01–$0.05, so the price IS the trial
- **Rate limits:** Implicit (you can call as fast as you can pay)

## Notable / differentiators

- One of the **first ~20 production MCP servers using x402 micropayments**.
- **Industry-first GEO score** — no other naming tool measures AI findability.
- Self-describing 402 responses: agents discover the catalog from any unauthenticated call.
- Remote Streamable HTTP, zero install, no `.mcpb` download.
