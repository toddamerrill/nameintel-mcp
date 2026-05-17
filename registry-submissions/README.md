# NameIntel — Registry Submissions

This directory contains the exact text and submission path for every MCP / x402 / agent-discovery registry NameIntel should be listed in. Each file is the canonical version we paste into the registry's submission form or PR template.

**Status legend:**
- `[ ]` not yet submitted
- `[~]` submitted, awaiting review
- `[x]` live in registry

## Live

- [x] [**mcp-registry.md**](./mcp-registry.md) — **Official MCP Registry** as `io.nameintel/server`. The protocol-level discovery layer that MCP clients query at runtime. Highest-leverage placement available.

## In review

- [~] [awesome-mcp-servers.md](./awesome-mcp-servers.md) — `punkpeye/awesome-mcp-servers` (87K stars). [PR #6512](https://github.com/punkpeye/awesome-mcp-servers/pull/6512) open with the `🤖🤖🤖` fast-track suffix.

## Auto-cataloged (no PR)

- [ ] **coinbase/x402 Bazaar** — x402's Bazaar discovery layer auto-catalogs services when payments settle through a Bazaar-supporting facilitator (Coinbase's does). To trigger: flip `X402_MODE=enforce`, include the `bazaar` extension in our 402 responses, take a first real payment. Until then we're invisible.

## Not yet submitted (P1)

- [ ] [mcp-so.md](./mcp-so.md) — MCP.so community marketplace. The backing repo (`chatmcp/mcp-directory`) uses SQL-backed data; submission is likely via the web form at https://mcp.so/submit.
- [ ] [mach-alliance.md](./mach-alliance.md) — MACH Alliance MCP Registry (enterprise credibility). Web form.
- [ ] [azure-api-center.md](./azure-api-center.md) — Microsoft Azure API Center MCP catalog. Requires a Microsoft publisher account.
- [ ] [x402-org.md](./x402-org.md) — x402.org ecosystem showcase. Submission path appears to be a Google Form (https://x402.org/ecosystem → "Contact").

## Not yet submitted (P2)

- [ ] [kong-mcp-registry.md](./kong-mcp-registry.md) — Kong API gateway MCP registry.
- [ ] [mcp-compass.md](./mcp-compass.md) — Semantic / NPX-based MCP discovery (PR to project's index repo).
- [ ] [awesome-x402.md](./awesome-x402.md) — Community x402 GitHub list. Need to locate canonical repo.
- [ ] [anthropic-aaif.md](./anthropic-aaif.md) — Anthropic AAIF Registry. Submission flow goes live when the registry is implemented.

## Cross-registry constants

- **Name:** NameIntel
- **MCP server name in registry:** `io.nameintel/server`
- **Tagline:** Clear to launch — name intelligence for the agent economy
- **MCP endpoint:** `https://mcp.nameintel.io/mcp` (Streamable HTTP)
- **REST API base:** `https://api.nameintel.io`
- **Homepage:** `https://nameintel.io`
- **Public repo:** `https://github.com/toddamerrill/nameintel-mcp` (MIT)
- **License:** MIT (public mirror); proprietary commercial pay-per-call (service)
- **Author:** Silverback CTO / CogleGroup
- **Contact:** todd@silverbackcto.com
- **Pricing:** $0.01–$0.05 USDC per call via x402 (Base + Solana)
- **Tools:** score_name, check_domain, check_trademark, check_social, check_geo
- **Differentiator:** First naming/branding MCP server. Industry-first GEO (AI findability) score. x402 micropayments — no signup, no API keys.
