# x402.org Ecosystem — Ready-to-paste Submission

**Form URL:** https://docs.google.com/forms/d/e/1FAIpQLSc2rlaeH31rZpJ_RFNL7egxi9fYTEUjW9r2kwkhd2pMae2dog/viewform
**Estimated time:** 3–5 minutes
**Recipient:** Coinbase / x402 ecosystem team

The form is generic-purpose (labelled "Contact"), so you'll likely paste most of this into a free-form message field. Lead with the punchline, then the detail.

---

## Subject / first line

> Submitting NameIntel to the x402 ecosystem showcase — one of the first naming/branding services to ship with x402 pay-per-call.

## Body (paste verbatim)

> Hi x402 team,
>
> I'd like to submit NameIntel to the x402 ecosystem listing at https://x402.org/ecosystem.
>
> **What it is:** NameIntel is a brand-name intelligence service that scores names across five dimensions — domain availability, USPTO trademark conflict, social handle availability, SEO strength, and AI findability (GEO score — industry-first). It's published as an MCP server and a parallel REST API; both use x402 as the only authentication mechanism.
>
> **Why it's a good showcase for x402:**
>
> - Pay-per-call pricing from $0.01 to $0.05 USDC across six priced endpoints — a category that genuinely cannot exist on card rails (Stripe's smallest viable transaction is ~$0.50 net of fees).
> - Self-describing 402 responses: when an agent calls an endpoint without payment, the 402 returns the *full price menu* with every other endpoint's price plus cheaper alternatives. The error response doubles as a discovery surface.
> - Dual-rail by design: Base (primary, via the Coinbase CDP facilitator at `api.cdp.coinbase.com/platform/v2/x402`) and Solana (planned for v1.1).
> - Live in the official MCP Registry as `io.nameintel/server`.
>
> **Links:**
>
> - Site: https://nameintel.io
> - REST API: https://api.nameintel.io (OpenAPI: /openapi.json)
> - MCP server: https://mcp.nameintel.io/mcp (Streamable HTTP)
> - x402 manifest: https://api.nameintel.io/.well-known/x402
> - Public mirror repo (MIT): https://github.com/toddamerrill/nameintel-mcp
>
> Happy to provide a case study / metrics / quote for the Coinbase developer blog if useful — this is exactly the kind of agent-economy primitive x402 enables.
>
> Built by Silverback CTO and CogleGroup using the Velocity Process.
>
> — Todd Merrill (todd@silverbackcto.com)

## Likely form fields & answers (Google Forms default contact form pattern)

- **Name:** Todd Merrill
- **Email:** todd@silverbackcto.com
- **Company / project:** Silverback CTO — NameIntel
- **Type of inquiry:** Ecosystem listing / showcase submission
- **Message:** *(use the body above)*

## Follow-up channels if no response in 1–2 weeks

- **Coinbase Developer Relations:** the team is active on Twitter/X (@CoinbaseDev) and the x402 GitHub repo (`github.com/coinbase/x402` issues).
- **GitHub issue:** open a low-key issue at `coinbase/x402` describing the submission and linking to nameintel.io. Their team triages there.
- **Bazaar auto-discovery:** once we flip `X402_MODE=enforce` and take a real settled payment via the Coinbase facilitator, NameIntel should appear in their `/discovery/resources` endpoint automatically per the [Bazaar spec](https://github.com/coinbase/x402/blob/main/docs/extensions/bazaar.mdx). That bypasses the form entirely once we go live.
