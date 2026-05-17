# Kong MCP Registry Submission

**Status:** [ ] not yet submitted
**Submission path:** https://konghq.com/products/mcp-registry — check current submission flow (likely a Kong Konnect account + a publish-to-registry form, or a GitHub PR to a manifest repo)
**Owner:** Todd Merrill
**Submission URL:** _fill in after submission_

---

## Server profile

**Server name:** NameIntel
**Publisher:** Silverback CTO
**Category:** Business Intelligence / Branding
**Endpoint:** `https://mcp.nameintel.io/mcp`
**Transport:** Streamable HTTP
**Auth:** x402 (pay-per-call USDC, no API key)

## Manifest

Point Kong's discovery layer at the canonical `/.well-known/mcp.json`:
`https://api.nameintel.io/.well-known/mcp.json`

## Tool catalog (5 tools)

| Tool | Description | Price (USDC) |
|---|---|---|
| `score_name` | 5-dimensional brand-name score | 0.05 |
| `check_domain` | Domain availability across TLDs | 0.01 |
| `check_trademark` | USPTO trademark conflict screen | 0.01 |
| `check_social` | Handle availability across 12+ platforms | 0.01 |
| `check_geo` | AI findability score | 0.03 |

## Why list in Kong's registry

Kong's MCP registry emphasizes dynamic tool discovery via API gateway patterns. NameIntel is a strong fit because:

- All tool metadata is served from a single `/.well-known/mcp.json` manifest — Kong's gateway can pull and refresh capabilities without manual updates.
- Pricing is part of the manifest, enabling Kong-side billing or cost reporting for downstream consumers.
- The 402-as-menu response shape pairs well with Kong rate-limiting and consumer attribution patterns.

## Contact

Todd Merrill — todd@silverbackcto.com
