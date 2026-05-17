# MCP Compass Submission

**Status:** [ ] not yet submitted
**Submission path:** MCP Compass is an NPX-based semantic discovery tool. Submission is typically a PR to the project's index repo. Check https://github.com/liuyoshio/mcp-compass (or the current canonical location) for the submission format.
**Owner:** Todd Merrill
**Submission URL:** _fill in after submission_

---

## Why MCP Compass matters

MCP Compass surfaces tools to agents via *natural-language queries* over embeddings rather than keyword search. The tool descriptions we register here are our agent-facing SEO.

## Submission entry

**Server name:** NameIntel
**Server URL:** `https://mcp.nameintel.io/mcp`
**Transport:** Streamable HTTP
**Auth note:** x402 pay-per-call. Agent's runtime needs an x402-compatible wallet; payments are $0.01–$0.05 USDC per call on Base or Solana.

## Semantically-rich tool descriptions (written for embedding similarity)

```yaml
tools:
  - name: score_name
    summary: |
      Evaluate a brand name. Score a business name. Check if a name is
      available. Validate a startup name. Trademark conflict screen.
      Domain availability check. Social handle availability across
      platforms. SEO keyword strength. AI findability score. Composite
      brand-name score across five dimensions returning 0-100 with
      sub-scores and a verdict for go / no-go decisions.
    price_usdc: "0.05"

  - name: check_domain
    summary: |
      Domain availability check. Look up domain registration status.
      Check .com, .io, .ai, .app, .co, .dev availability. Domain name
      search. Premium domain detection. Find takeable domains for a
      brand name across TLDs.
    price_usdc: "0.01"

  - name: check_trademark
    summary: |
      USPTO trademark search. Trademark conflict check. Brand legal
      clearance. Nice class matching. Risk assessment for registering a
      brand name. Search live trademarks and pending applications for
      conflicts with a candidate name.
    price_usdc: "0.01"

  - name: check_social
    summary: |
      Social media handle availability check. Username availability
      across X, Twitter, Instagram, TikTok, LinkedIn, YouTube, GitHub,
      Facebook, Reddit, Pinterest, Threads. Verify a brand can claim
      consistent handles across platforms.
    price_usdc: "0.01"

  - name: check_geo
    summary: |
      AI findability score. Generative engine optimization (GEO) for
      brand names. Score how likely a brand name surfaces correctly in
      answers from ChatGPT, Perplexity, Claude, and Gemini. Entity
      collision, semantic distinctiveness, corpus saturation, phonetic
      clarity. The only API that scores this dimension.
    price_usdc: "0.03"
```

## Why broaden the semantic surface

These tool summaries cover the surrounding semantic territory deliberately. An agent asked "is X a good company name" or "check if my brand is taken" should match `score_name`. Agents asked about "trademark deep search" or "USPTO clearance" should match `check_trademark`. Vector retrieval rewards descriptive density, not keyword purity.

## Contact

Todd Merrill — todd@silverbackcto.com
