# Agent Discovery Strategy

**A working memo on how NameIntel — and every Velocity Project after it — gets found, evaluated, and chosen by agents.**

Author: Todd Merrill (Silverback CTO)
Date: May 2026
Status: Strategic working draft

---

## Executive Summary

NameIntel is a fine human product with an unfinished agent product. We've shipped a paid REST API, an MCP server, x402 middleware, an llms.txt, a schema.org block, and an AI-friendly robots.txt. By 2025-era SEO standards this is best-in-class. By the standards of *agent-native commerce* — what Clawbot, Claude, ChatGPT agents, Replit agents, and a long tail of vertical bots will do over the next 12-24 months — it scores about a 4 out of 10. We have the surfaces. They aren't yet *self-describing, machine-priced, registry-listed, or composable.*

Three things follow from that:

First, there is a near-term build sprint to close the discoverability gap on NameIntel itself. Most of it is a long afternoon of work — not a quarter — and it makes the GTM submissions in `gtm-strategy.md` actually land.

Second, the same pattern generalizes. Every Velocity Project we ship — PatentFlow, GEOPress, the next ones — will face an identical question: how does an agent find this and decide to pay for it? Codifying the answer once, as a reusable spec, turns "agent-native" from a slogan into infrastructure. I've drafted that spec below as the **Velocity Discoverability Spec v1**.

Third, this is a real positioning opportunity. There is essentially no canonical writing yet on agent service discovery, x402 micropayment economics, or the reputation primitives the agent economy will need. We are unusually well-positioned to write the canon — we are building one of the first 50 paid x402 MCP services in the world, we own the GEO category language, and we have four credible audiences to address. The article portfolio at the back of this memo gives us 5 pieces, sequenced and channel-mapped.

The crypto angle deserves its own treatment because it's not a sidebar — micropayments are the load-bearing wall under all of this. A world where agents do tiny tasks for hire requires settling tiny payments. Stripe can't do that economically. USDC on Base/Solana can. The first writers to articulate that thesis cleanly own a category.

---

## Part 1 — Where NameIntel Stands Today

The audit (see appendix in spirit; bullets only where they earn it):

We have an llms.txt, but it reads as a human marketing README — features, target audience, pricing tiers in prose. It does not advertise the MCP endpoint URL, the per-tool x402 prices, the API base URL, or the authentication method in any form an agent can parse. The robots.txt explicitly admits GPTBot, ClaudeBot, PerplexityBot, anthropic-ai, and Googlebot — that part is correct — and it points to a sitemap that does not yet exist.

The schema.jsonld declares NameIntel as a `SoftwareApplication` with one `Offer` priced at zero. It does not declare the seven actual offers (full score, basic score, four single-dimension checks, GEO check) at their actual USDC prices. There is no `/.well-known/` directory at all — no `mcp.json`, no `x402` manifest, no OpenAI-style `ai-plugin.json`. The `/health` endpoint returns `{status: 'ok', service: 'nameintel', version: '1.0.0'}` with no capability inventory, no pricing, no SLA hints, no changelog pointer. The 402 response from x402 middleware lists payment chains and amounts but doesn't surface the menu — an agent that gets billed $0.05 for a full score has no way to learn that a $0.02 basic score exists, or that domain-only is $0.01. There is no served OpenAPI spec, no machine-readable changelog, and no evidence in the repo that we've actually submitted to MCP.so, awesome-claude-dxt, MACH Alliance, Azure API Center, Kong Registry, Anthropic AAIF, or MCP Compass — all named in the GTM doc as P1 targets.

The MCP server itself is solid. Five tools, clear human-readable descriptions, sensible names. It will work the moment a human installs it. What it lacks is the reputation, registry presence, and machine metadata that lets an agent *find* it without a human in the loop.

The x402 middleware is currently in `bypass` mode. That is correct for a pre-launch state. The 402 enforcement path exists and returns the right JSON shape, but it doesn't yet integrate with the Coinbase Facilitator for verification (`TODO` on line 71 of `src/api/middleware/x402.ts`). The receiver wallet addresses come from environment variables that are not yet populated.

**Bottom line:** Humans can find and buy NameIntel today through a press launch, an HN post, and a few directory submissions. Agents cannot autonomously find, price, or pay for it without a human first telling them it exists. Closing that gap is the work of the next two weeks.

---

## Part 2 — The Agent Discovery Stack: Today and Where It's Going

### What exists today (May 2026)

There are roughly seven layers an autonomous agent can use to find a paid service like ours, and they overlap messily.

**The MCP registry layer** — MCP.so, Glama, Smithery, Composio, Pipedream, awesome-mcp-servers, awesome-claude-dxt, Anthropic's own registry. These are mostly curated lists or lightly-API-fronted catalogs. Discovery is keyword search by humans wiring up Claude Desktop or Claude Code; agents themselves rarely query them at runtime. Submission is manual, often a GitHub PR.

**The well-known endpoint layer** — `/.well-known/ai-plugin.json` (the OpenAI Plugin standard, largely deprecated), `/.well-known/mcp.json` (emerging), `/.well-known/x402` (proposed in the x402 ecosystem), and the older `/.well-known/security.txt` and `humans.txt` traditions. This layer is *agent-native* in spirit — an agent that knows your domain can probe these paths without a registry lookup. Adoption is early but it's the cheapest discoverability surface to add.

**The llms.txt convention** — Anthropic-promoted, Apple/Mintlify-adopted. Currently mostly a markdown summary for LLM context windows. Beginning to evolve into a manifest format with structured pricing and endpoint metadata. This is the most underrated surface because it sits at a path agents are already trained to look at.

**The schema.org structured data layer** — `SoftwareApplication`, `Service`, `Offer`, `WebAPI`, `EntryPoint`. This is what Google, Bing, and Perplexity actually index. Agents that fall back to web search land on these signals.

**The OpenAPI / AsyncAPI layer** — old-school but still load-bearing. An OpenAPI spec at a predictable URL (`/openapi.json`) is what serious agent frameworks (LangChain, Mastra, Vercel AI SDK) auto-import to generate tool wrappers.

**The training-data layer** — what models *already know about you* from their pretraining cut-off. This is where GEO (the practice, not our score) lives. Being on Wikipedia, Stack Overflow, GitHub README mentions, conference talks, and high-PageRank blogs makes you part of the model's prior.

**The x402 / payment-rail directories** — emerging. x402.org will list services. Coinbase CDP has a directory. There will be others. Being early here is cheap and valuable.

These seven layers are how agents find services *today*. None of them is sufficient alone. A serious agent-native service shows up in all seven.

### Where it's going (12-36 months out)

The current stack is essentially "the agent reads the same web a human does, plus a few new files." That breaks at scale. Three shifts are already visible.

**From lookup to bidding.** Today an agent searches a registry. Tomorrow an agent posts a job — *"score the brand name 'Lumina' for a wellness DTC brand, max budget $0.10, deadline 30 seconds"* — and services bid. This is the reverse marketplace pattern, and it requires a new primitive: a standardized job-description format and an auction protocol. Google's Agent2Agent (A2A) spec, Cisco's AGNTCY, and the Agent Network Protocol (ANP) are all early stabs. Whoever wins, services will need to advertise *not just what they do but what they're willing to bid on.* That's a step beyond MCP tool descriptions.

**From keyword to embedding.** Agents don't search by keyword the way humans do. They search by semantic similarity over embeddings. This means tool descriptions need to be written for vector retrieval — not only "score a brand name" but the surrounding semantic territory ("evaluate a name", "check if a name is taken", "validate a brand", "trademark conflict screening", "naming a startup"). Registries will start indexing on embedding similarity rather than tag matches. Services that don't write for that lose discoverability without knowing why.

**From caveat emptor to reputation graphs.** When agents pay real money to other services, they will need trust signals. On-chain reputation (verifiable execution proofs), cross-service vouching ("PatentFlow says NameIntel is reliable"), uptime attestation, and dispute resolution will become first-class. The earliest version of this is just *being cited by other services in their docs* — a primitive PageRank for agents. We can game that constructively by cross-linking the Velocity portfolio.

**From per-call billing to streaming and bundles.** x402 today is per-request micropayments. Soon: streaming payments (pay per millisecond of LLM time), prepaid bundles ("$5 for 100 score calls, redeemable across NameIntel + PatentFlow"), and fractional pay-per-success (only billed if the agent's downstream task actually succeeded). The financial primitives are evolving as fast as the discovery ones.

**From service to composable pipeline.** Agents won't call NameIntel in isolation. They'll chain it: generate names with one service, score them with NameIntel, run trademark deep-dive with PatentFlow, write copy with another service. To be choosable as a *link in a chain*, NameIntel needs to advertise input/output schemas in machine-readable form so the orchestrator can wire it up automatically. This is a stronger requirement than "have an OpenAPI spec" — it's "have a self-describing contract that composes."

The pattern across all five shifts: **the units get smaller, the metadata gets richer, the trust gets harder, and the speed at which a service is chosen-or-skipped goes up by orders of magnitude.** Services that can't be machine-read in 200 milliseconds won't be chosen.

---

## Part 3 — The Velocity Discoverability Spec v1

This is the reusable pattern. Every Velocity Project should ship every item on this list before public launch. NameIntel becomes the v1 reference implementation; PatentFlow and GEOPress get it on day zero.

The spec has three layers: **Advertise, Address, Accept.** What you do, where to reach you, how to pay you.

### Advertise (machine-readable identity and capabilities)

A `/.well-known/mcp.json` at the apex domain, declaring: server URL (HTTP transport), tool list with descriptions, per-tool pricing in USDC, payment method (`x402` + chain list), authentication scheme, free-tier semantics, link to OpenAPI spec, link to changelog, link to status page. This is the file a curious agent fetches first.

A `/.well-known/x402` manifest declaring: accepted chains, receiver addresses, facilitator URLs, supported currencies, refund policy, dispute contact. Lets x402-aware agents discover payment terms without parsing a 402 response first.

An `llms.txt` rewritten as a machine-leaning manifest: same human prose at the top, but with a structured block at the bottom containing the same fields as `/.well-known/mcp.json` in YAML. Agents that fall back to llms.txt (more common than well-known probing today) get the same data.

A `schema.jsonld` with a *complete* `Offer` array — every priced endpoint, every tier, every USDC amount. Schema.org is what Perplexity and Bing index, and we're invisible to them on pricing today.

A served `/openapi.json` (or `/openapi.yaml`) at the root of the API subdomain, generated from the route definitions. LangChain, Mastra, Vercel AI SDK, and most agent frameworks consume this directly.

### Address (where to reach you, how to verify you)

A `/health` endpoint that returns more than "ok" — version, uptime, region, capability inventory (tool list with current pricing), changelog URL, status page URL. An agent burning time deciding whether to call you can hit this in 50ms and decide.

A `/changelog.json` (or RSS) that publishes additions, deprecations, and breaking changes. Agents that have you wired into a pipeline need to detect schema drift.

A status page (StatusGator-style or simple JSON at `/status.json`) declaring uptime over the last 30/90 days. Reputation primitive #1.

A robots.txt that allows GPTBot, ChatGPT-User, ClaudeBot, anthropic-ai, PerplexityBot, OAI-SearchBot, Bytespider, Applebot-Extended, and Google-Extended. NameIntel does this; the rest of Velocity should.

A real `sitemap.xml` (we point to one but don't have it).

### Accept (self-describing payment and attempt semantics)

A 402 response that returns the *menu*, not just the bill. When an agent hits `/api/v1/score` without payment, the 402 should include: this endpoint's price, all available endpoints with prices, available bundles, alternative cheaper endpoints that might fit the use case ("if you only need domain availability, `/api/v1/check/domain` is $0.01"), supported chains and currencies, link to `/.well-known/x402`. Make the error response a discovery surface.

Sample response payloads embedded in error messages — when an agent sends bad input, the error tells it what good input looks like, with a working example. This is the equivalent of Stripe's famously good error messages, ported to the agent era.

A documented free-tier protocol — how an agent can take a *single* trial call without payment, with explicit headers (e.g., `X-Trial-Request: true` and a per-IP daily ceiling). Lets agents probe-then-buy without humans in the loop.

### Distribution (the work outside the codebase)

Submission templates committed to the repo (`./registry-submissions/mcp.so.md`, `./registry-submissions/awesome-claude-dxt.md`, etc.) with the exact text and PR links to every directory we should be in. Future-Velocity-Todd shouldn't have to remember this list.

A "powered by" footer-link policy across the Velocity portfolio — every Velocity service mentions every other Velocity service in the docs and at the bottom of the marketing site. Cheap PageRank, cheap trust graph, cheap cross-sell.

A press-and-blog kit committed to each repo with: launch announcement template, X/LinkedIn posts, the canonical blog post explaining what the service does, an MCP install GIF, and a link list of every place we've been mentioned.

---

That's the spec. Twelve-ish items. Half a day of work per project once the templates exist. Doing it once, then forking the templates, is the single highest-leverage move we can make on agent discoverability across the Velocity portfolio.

---

## Part 4 — The Article Portfolio

Five pieces, sequenced. Each one is independently shippable, but together they establish Silverback as the canonical voice on agent service discovery and the agent micropayment economy. NameIntel is the recurring case study across all of them — "we built this, and here's what it taught us."

### Article 1 — "Your API Has No Idea Agents Exist"

**Audience:** Technical founders and CTOs.
**Channel:** dev.to, Hacker News, Substack, the Anthropic dev blog if pitched.
**Hook:** A two-paragraph opener narrating an autonomous agent trying to find a paid name-scoring service today. It can't. It falls back to scraping. It loses three minutes on a task that should have taken three seconds. *Your API is the reason.*
**Thesis:** Most APIs in 2026 are still designed for human integrators. Agents need a different surface area: machine-readable manifests, self-describing errors, registry presence, embedding-friendly tool descriptions. The piece walks through the **Velocity Discoverability Spec** as a practical fix-list, with NameIntel before/after as the worked example.
**Why it lands:** Concrete, opinionated, immediately actionable. Goes well in front of HN because it's a builder's piece with a specific spec, not a vibe piece.
**Headline candidates:**
- *"Your API Has No Idea Agents Exist. Here's the Fix."*
- *"The /.well-known/ Files Your Agent-Native Service Is Missing"*
- *"What I Learned Shipping the 18th x402 MCP Server in the World"*

### Article 2 — "USDC for Tiny Tasks: Why x402 Wins the Agent Economy"

**Audience:** Crypto / web3 / x402 ecosystem; Coinbase CDP devs; Base and Solana communities.
**Channel:** Mirror.xyz, the Coinbase blog if pitched as a customer story, the x402.org blog, Bankless newsletter.
**Hook:** Stripe's smallest viable transaction is about $0.50 net of fees. NameIntel charges $0.05 for a name score. Do the math.
**Thesis:** The agent economy will run on transactions one to three orders of magnitude smaller than what credit-card rails can settle economically. USDC on Base/Solana settles a $0.01 trademark check with sub-cent fees and sub-second finality. That's not a 10% improvement — it's a different category of commerce. Walk through what we built, the actual cost stack per call, and why per-task micropayments enable services that just couldn't exist on Stripe.
**Why it lands:** This is the strongest crypto narrative going right now and it's underwritten. There are very few real production examples of x402 in commerce; we are one. Coinbase's content team is hungry for case studies.
**Headline candidates:**
- *"$0.05 Per Call: The Math That Makes the Agent Economy Possible"*
- *"Stripe Can't Settle a Two-Cent Trademark Check. USDC Can."*
- *"What I Learned Building an x402 Service Before Anyone Was Ready For It"*

### Article 3 — "MCP Manifests Are the Next robots.txt"

**Audience:** MCP ecosystem, Anthropic devrel, agent platform builders, the people maintaining MCP.so / Glama / Smithery / Composio.
**Channel:** Substack, Anthropic's developer newsletter (pitched), MCP discord cross-post, LinkedIn for Anthropic eyeballs.
**Hook:** robots.txt was a hack that became a standard because everyone needed to talk to crawlers and someone had to go first. /.well-known/mcp.json is the same hack waiting to happen for agents. Here's a proposed schema.
**Thesis:** Argue for a standardized `/.well-known/mcp.json` with structured pricing, capability tags, payment manifest, free-tier semantics, and SLA hints. Propose the schema. Show NameIntel's implementation as the reference. Invite ecosystem feedback. *This is a thought-leadership move designed to get cited.*
**Why it lands:** Anthropic and the MCP community are actively standardizing right now. A well-formed proposal with a working reference implementation has a real chance of being adopted or cited. Even if it doesn't, it positions Silverback as a voice in the MCP standards conversation.
**Headline candidates:**
- *"A Proposal: /.well-known/mcp.json"*
- *"MCP Needs a Manifest Standard. Here's a Strawman."*
- *"How Should Agents Discover Paid MCP Services? A Concrete Proposal."*

### Article 4 — "GEO 2.0: When Agents Pick Your Vendors, What Makes You Findable?"

**Audience:** Enterprise marketers, branding leaders, agency principals, in-house legal/IP teams. Less technical.
**Channel:** LinkedIn (long-form), branding industry trade pubs (Branding Magazine, Adweek if pitched), Silverback's own Substack.
**Hook:** Last year you optimized your brand to rank in ChatGPT answers. This year you have to optimize for agents who don't ask ChatGPT — they pick a vendor and pay them. The rules changed.
**Thesis:** GEO ("generative engine optimization") was about being mentioned in AI answers. The next layer is being *chosen by autonomous agents* who run tasks. That's a different optimization target — registry presence, machine-readable pricing, reputation primitives, embedding-friendly descriptions. Use NameIntel both as proof-of-concept (we built one of the first agent-native paid services) and as product (our GEO score evaluates exactly this kind of findability for brand names).
**Why it lands:** This is the cross-sell piece. It establishes the *category* — "Agent Discoverability" or "GEO 2.0" — and positions NameIntel and the Velocity portfolio as the firm that thinks about it. Less technical, broader audience, opens enterprise conversations.
**Headline candidates:**
- *"GEO 2.0: When Agents Pick Your Vendors, You'd Better Be Findable"*
- *"Your Brand Has to Be Choosable by a Bot Now. Here's What That Means."*
- *"After SEO, After GEO: Welcome to ADO"* (Agent Discoverability Optimization)

### Article 5 — "The Velocity Discoverability Spec"

**Audience:** All four. This is the canonical-reference piece.
**Channel:** Silverback Substack as the home, with cross-posts as appropriate. Open-source the spec as a GitHub repo (`silverbackcto/agent-discoverability-spec`) so it's forkable and citable.
**Hook:** "We've shipped one agent-native paid service. Here's the checklist we wish we'd had on day one. Use it. Fork it. Send PRs."
**Thesis:** The full spec from Part 3, written up as a standalone reference with the rationale for every item. Becomes the linkable artifact behind every other article in this series — *"see the full Velocity Discoverability Spec for the complete checklist."*
**Why it lands:** Open-sourcing the spec turns Silverback into the apparent maintainer of a category. That's a long compounding asset. Even if no one else adopts it formally, it's the canonical write-up we point everyone to.

### Suggested sequencing

Ship Article 1 first — it has the broadest audience and the most concrete fix-list, gets us HN attention. Article 2 a week later, while the x402 conversation is hot. Article 3 (the MCP proposal) two weeks after that, timed to whichever Anthropic MCP announcement comes next so we can ride the news cycle. Article 4 (GEO 2.0) lives on a longer horizon — write it carefully, place it where enterprise eyeballs are. Article 5 (the spec) goes up alongside Article 1 on day one as the reference artifact, gets cited by all the others.

---

## Part 5 — The Crypto / Micropayments Thesis (Worth Its Own Treatment)

The crypto angle is not a sidebar to agent discovery — it is the load-bearing wall. Here's the argument distilled, because it'll show up in three of the five articles and we should be able to state it crisply.

The fundamental shift agents force is **transaction granularity collapsing by 2-3 orders of magnitude.** A human buys software in $50/month subscriptions. An autonomous agent doing one specific task has no use for a subscription — it wants to pay exactly for what it consumes, and what it consumes is *a single API call worth one to ten cents.* Stripe's economics break down below about 50 cents net. PayPal's are worse. ACH is hopeless. Card-not-present rails were designed for human commerce and they cannot, even in principle, settle a one-cent transaction profitably. The math just doesn't work — interchange alone eats it.

USDC on Base settles a $0.01 transaction in under a second with fees measured in fractions of a penny. USDC on Solana is faster and cheaper still. **This is not an incremental improvement. It is the difference between a market that exists and a market that does not.** Without this primitive, agent commerce stays trapped in subscription models that don't fit how agents actually work.

x402 is the wrapper that makes this useful. HTTP 402 was reserved for "Payment Required" 30 years ago and never used. Coinbase resurrected it as a protocol: an API returns 402 with a payment manifest, the client (or its wallet) pays in USDC, retries with a payment header, gets the response. It is exactly the right grain — per-request, self-describing, chain-agnostic, self-authenticating (the payment IS the auth).

The downstream consequences are bigger than they first appear:

**Subscription pricing becomes a fallback, not a default.** For tasks an agent does once a month, pay-per-call is cheaper. Subscriptions survive only for usage patterns where amortization actually wins.

**Free tiers get rethought.** A $0.01 call doesn't need a free tier — the price IS the free tier. The frictionless probe becomes a paid call, not a signup form.

**Auth simplifies massively.** OAuth, API keys, JWTs are mostly there to determine *who's allowed to call this and how much they owe.* If the answer is always "anyone who pays," then auth collapses into payment. NameIntel's API has no signup, no API keys, no rate-limit-per-account. Just send USDC.

**New service categories become viable.** A $0.001 trademark deep-search across all jurisdictions. A $0.0005 domain availability check across 200 TLDs. A $0.01 sentence-by-sentence brand-safety scan. None of these can exist on credit cards. All of them can exist on x402.

**Reputation becomes the new gating mechanism.** When auth doesn't gate access, *trust* gates access. Whose service should the agent pay? On-chain reputation, cross-service vouching, and dispute resolution become the load-bearing layer that auth used to be.

That's the thesis. It is the argument I want to make publicly because it is correct and underwritten. The first wave of writers to articulate it cleanly will own the framing for the next several years.

---

## Part 6 — Recommended 30/60/90

**Next 30 days.** Ship the Velocity Discoverability Spec changes for NameIntel. Specifically: complete `/.well-known/mcp.json`, complete `/.well-known/x402`, rewrite `llms.txt` with a structured block, expand `schema.jsonld` to cover all seven offers, expand `/health` to include the capability inventory, expand the 402 response to return the menu, ship `/openapi.json`, ship `/changelog.json`, create the actual `sitemap.xml`. Submit to MCP.so, awesome-claude-dxt, MACH Alliance, Azure API Center, Kong Registry, x402.org directory, MCP Compass. Publish Article 1 ("Your API Has No Idea Agents Exist") and Article 5 (the spec, open-sourced).

**Days 30-60.** Publish Article 2 (the USDC micropayments piece) targeted at Coinbase / x402 community. Publish Article 3 (the /.well-known/mcp.json proposal) timed to the next MCP news beat. Stand up the Velocity Discoverability Spec as a public repo with PR templates so we can accept community contributions. Add cross-links across the Velocity portfolio sites — every service mentions every other service.

**Days 60-90.** Publish Article 4 (GEO 2.0) for the enterprise/branding audience. Replicate the spec on PatentFlow and GEOPress. Begin reputation primitive work — status page, public uptime numbers, changelog discipline, cross-service "trusted by" badges. Begin watching the A2A / AGNTCY / ANP standards work and pick the first one to support; aim to be among the first 10 services that implement it.

The cumulative effect: by August 2026 NameIntel is the most discoverable paid MCP service in its category, the Velocity portfolio has a unified discoverability story, Silverback owns the canonical writing on agent service discovery and x402 micropayment economics, and the spec is the artifact people cite when they're trying to make their own services agent-native.

That's the play.

---

## Appendix — Open Questions

A few things I haven't resolved that we should discuss before I commit to any of this in print.

How public do we go on x402 implementation details? There's a tradeoff between thought leadership and giving competitors a free playbook. My instinct is to publish — the moat is execution and brand, not the spec.

Do we want to file a Velocity Discoverability Spec as an actual standards proposal somewhere (W3C? IETF? IANA?) or keep it as an opinionated GitHub repo? Standards work is slow and reputational; a strong opinionated repo can win without it.

Do we partner with anyone on Article 3 (the /.well-known/mcp.json proposal)? Co-bylining with someone in the MCP ecosystem (Glama, Smithery, Composio) would amplify reach but slow things down. Solo is faster and more clearly attributable.

What's our position on Anthropic's first-party agent registry when it ships? My guess is we should be in it on day one and write a piece about being among the first cohort. Worth being ready for.
