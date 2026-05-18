# NameIntel — Registry Submissions

This directory holds the canonical text + submission path for every registry NameIntel is or should be listed in. PR templates live as flat files. Web-form / Typeform / Google-Form packets — the ones we can't submit programmatically — live in [`forms/`](./forms) with copy-paste-ready field values.

**Status legend:**
- `[ ]` not yet submitted
- `[~]` submitted, awaiting review
- `[x]` live in registry

## Live ✅

- [x] [**mcp-registry.md**](./mcp-registry.md) — **Official MCP Registry** as `io.nameintel/server`. The protocol-level discovery layer that MCP clients query at runtime. DNS-verified via Route 53 TXT under `io.nameintel.*`. Highest-leverage placement.

## In review ⏳

- [~] [awesome-mcp-servers.md](./awesome-mcp-servers.md) — `punkpeye/awesome-mcp-servers` (87K stars). [PR #6512](https://github.com/punkpeye/awesome-mcp-servers/pull/6512) open with the `🤖🤖🤖` agent fast-track suffix.

## Auto-cataloged (no PR) 🔄

- [ ] **coinbase/x402 Bazaar** — x402's Bazaar discovery layer auto-catalogs services once they take a settled payment through a Bazaar-supporting facilitator (Coinbase's does). Triggers automatically when `X402_MODE=enforce` is flipped on and the first transaction lands.

## Browser-only submissions (ready-to-paste packets in [`forms/`](./forms))

These three accept submissions via web forms only — they actively block automated traffic. Each linked packet has copy-paste-ready field values; open the form URL and work through the fields.

- [ ] [`forms/mach-alliance.md`](./forms/mach-alliance.md) — MACH Alliance MCP Registry. Open Typeform, no membership needed.
- [ ] [`forms/mcp-so.md`](./forms/mcp-so.md) — MCP.so directory. Browser submission (or PR to chatmcp/mcp-directory).
- [ ] [`forms/x402-org.md`](./forms/x402-org.md) — x402.org ecosystem showcase. Google Form contact.

## Not yet submitted (P2)

- [ ] [kong-mcp-registry.md](./kong-mcp-registry.md) — Kong API gateway MCP registry.
- [ ] [mcp-compass.md](./mcp-compass.md) — Semantic / NPX-based MCP discovery (PR to project's index repo).
- [ ] [awesome-x402.md](./awesome-x402.md) — Community x402 list (need to locate canonical repo).
- [ ] [anthropic-aaif.md](./anthropic-aaif.md) — Anthropic AAIF Registry. Submission flow goes live when the registry is implemented.

## Dropped 🗑️

- ~~Azure API Center~~ — investigated and dropped. Azure API Center is a *tenant-scoped private catalog* that Microsoft customers run inside their own Azure subscriptions to track APIs they consume; it is **not** a public registry where external API/MCP providers submit listings. Wrong target.

## Cross-registry constants

- **Server name:** NameIntel
- **MCP server ID:** `io.nameintel/server`
- **MCP endpoint:** `https://mcp.nameintel.io/mcp` (Streamable HTTP)
- **REST API base:** `https://api.nameintel.io`
- **Homepage:** `https://nameintel.io`
- **Public repo:** `https://github.com/toddamerrill/nameintel-mcp` (MIT)
- **Author:** Silverback CTO / CogleGroup
- **Contact:** todd@silverbackcto.com
- **Pricing:** $0.01–$0.05 USDC per call via x402 (Base + Solana)
- **Tools:** score_name, check_domain, check_trademark, check_social, check_geo
- **Differentiator:** First naming/branding MCP server. Industry-first GEO (AI findability) score. x402 micropayments — no signup, no API keys.
