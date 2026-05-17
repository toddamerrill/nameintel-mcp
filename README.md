# NameIntel — MCP Server

> Clear to launch. Score brand names across domain, trademark, social, SEO, and AI findability — pay-per-call via x402 micropayments, no signup, no API keys.

NameIntel is a remote [Model Context Protocol](https://modelcontextprotocol.io) server that scores brand names across five dimensions and returns a composite 0–100 score with sub-scores and a verdict. The scoring engine is also reachable as a REST API. Every endpoint is priced in USDC and settled over the [x402 protocol](https://x402.org) on Base and Solana — there are no API keys to provision, no accounts to sign up for, and no rate-limit setup.

This repository is the public face of the project: install instructions, registry submissions, docs, and discovery manifests. The hosted service runs at [nameintel.io](https://nameintel.io).

## Quick install

**Claude Code:**
```bash
claude mcp add --transport http nameintel https://mcp.nameintel.io/mcp
```

**Claude Desktop:** Settings → Connectors → Add → paste `https://mcp.nameintel.io/mcp`.

That's it. There's no API key. The first time you call a tool the request returns HTTP 402 with the price (between $0.01 and $0.05 USDC depending on the tool); sign the payment with a Base or Solana wallet, retry, and it works. The Coinbase x402 facilitator verifies and settles in under a second.

## What it scores

| Dimension | What you get |
|---|---|
| **Domain** | Availability + pricing across .com, .io, .ai, .app, .co, .dev and other TLDs. Premium and auction detection. |
| **Trademark** | USPTO conflict screening. Exact matches, similar marks, Nice class analysis, risk level. |
| **Social** | Handle availability across 12+ platforms (X, Instagram, TikTok, LinkedIn, YouTube, GitHub, Threads, more). |
| **SEO** | Keyword strength, search-friendliness, and competition risk. |
| **GEO** | **Industry-first.** AI findability — how likely the name surfaces correctly in answers from ChatGPT, Perplexity, Claude, and Gemini. Entity collision, semantic distinctiveness, corpus saturation, phonetic clarity. |

## Tools

| Tool | Endpoint | Price |
|---|---|---|
| `score_name` | `POST /api/v1/score` | $0.05 USDC |
| Basic name score (no GEO) | `POST /api/v1/score/basic` | $0.02 USDC |
| `check_domain` | `POST /api/v1/check/domain` | $0.01 USDC |
| `check_trademark` | `POST /api/v1/check/trademark` | $0.01 USDC |
| `check_social` | `POST /api/v1/check/social` | $0.01 USDC |
| `check_geo` | `POST /api/v1/check/geo` | $0.03 USDC |

## REST API

If MCP isn't your fit, the same scoring engine is exposed as a REST API at `https://api.nameintel.io`. The OpenAPI 3.1 spec is served live at [`/openapi.json`](https://api.nameintel.io/openapi.json) and any framework that auto-imports OpenAPI (LangChain, Mastra, Vercel AI SDK) will wire up tool wrappers from it.

```bash
# Calling /api/v1/score without payment returns a 402 with the full menu:
curl -X POST https://api.nameintel.io/api/v1/score \
  -H "content-type: application/json" \
  -d '{"name": "Lumina"}'
# → HTTP 402, body is a JSON price menu + payment manifest link
```

## Machine-readable manifests

Every important surface is self-describing. Agents and discovery tools should prefer these over scraping prose.

- [/.well-known/mcp.json](https://api.nameintel.io/.well-known/mcp.json) — MCP server URL, tool inventory, prices
- [/.well-known/x402](https://api.nameintel.io/.well-known/x402) — payment manifest (chains, receivers, facilitators)
- [/openapi.json](https://api.nameintel.io/openapi.json) — OpenAPI 3.1 spec for the REST API
- [/changelog.json](https://api.nameintel.io/changelog.json) — version + breaking-change tracking
- [/health](https://api.nameintel.io/health) — liveness plus full capability inventory
- [llms.txt](https://nameintel.io/llms.txt) — LLM-readable summary with embedded YAML manifest

## Why this exists

When an AI agent helps a founder start a company, the first thing it needs is a clear-to-launch brand name. Today there is no agent-native tool for this — every existing naming tool requires a human in the loop, an API key, or a subscription. NameIntel is the tool that agent calls: one endpoint, USDC settlement, no friction.

The pricing also makes new use cases viable. A $0.01 trademark check or $0.05 brand-name score can't profitably exist on card rails — Stripe's smallest economically-viable transaction is around $0.50 net of fees. USDC on Base settles those amounts with sub-cent fees and sub-second finality, which is the difference between a market that exists and one that does not.

## Repository contents

| Path | What it is |
|---|---|
| [`registry-submissions/`](./registry-submissions) | Drafted submission packs for MCP / x402 / agent-discovery registries (MCP.so, MACH Alliance, Azure API Center, x402.org, awesome-mcp-servers, Kong, MCP Compass, AAIF). Exact text + submission paths. |
| [`docs/`](./docs) | Public-facing strategy and design docs — including [agent-discovery-strategy.md](./docs/agent-discovery-strategy.md), the rationale for the discovery surface this service ships. |
| `LICENSE` | MIT. |

## Status

| | Status |
|---|---|
| Service | ✅ Live at [api.nameintel.io](https://api.nameintel.io) and [mcp.nameintel.io](https://mcp.nameintel.io/mcp) |
| x402 mode | `bypass` (free during ecosystem launch). Will flip to `enforce` after live-payload verification. |
| Phase | 1 — MCP + API. Phase 2 (Stripe web app for human users) lands later. |

## Built with

Built by [Silverback CTO](https://silverbackcto.com) and CogleGroup using the [Velocity Process](https://silverbackcto.com) methodology.

- AWS App Runner + CloudFront + Route 53
- TypeScript + Express + the [MCP TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
- Claude (via AWS Bedrock) for the GEO score
- USPTO TSDR API for trademark screening
- Coinbase x402 facilitator for payment verification

## Contact

- Issues / suggestions: open an issue on this repo
- Commercial / agency: todd@silverbackcto.com
- Twitter/X: [@toddamerrill](https://twitter.com/toddamerrill)

## License

[MIT](./LICENSE)
