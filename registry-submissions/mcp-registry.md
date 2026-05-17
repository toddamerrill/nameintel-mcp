# MCP Registry (registry.modelcontextprotocol.io) — Live

**Status:** [x] **Live in the official MCP Registry**
**Submission path:** `mcp-publisher` CLI + DNS-verified `server.json`
**Owner:** Todd Merrill
**Live URL:** https://registry.modelcontextprotocol.io/v0/servers?search=nameintel
**Server name:** `io.nameintel/server`

---

## What landed

NameIntel is published in the **official MCP Registry** — the directory MCP clients query at runtime. This is the highest-leverage placement available: it's not a curated awesome list, it's the protocol-level discovery layer.

Published manifest at [`server.json`](../server.json) in the public mirror repo, mirrored here:

```json
{
  "$schema": "https://static.modelcontextprotocol.io/schemas/2025-12-11/server.schema.json",
  "name": "io.nameintel/server",
  "title": "NameIntel",
  "description": "Brand-name intelligence across 5 dimensions including AI findability. Pay-per-call via x402.",
  "version": "1.0.0",
  "repository": {
    "url": "https://github.com/toddamerrill/nameintel-mcp",
    "source": "github"
  },
  "websiteUrl": "https://nameintel.io",
  "remotes": [
    { "type": "streamable-http", "url": "https://mcp.nameintel.io/mcp" }
  ]
}
```

## How authentication was set up

DNS-based authentication via Route 53. The Ed25519 keypair lives at `~/.nameintel/mcp-publisher-key.pem` (0600). A TXT record on `nameintel.io` carries the public key:

```
nameintel.io. IN TXT "v=MCPv1; k=ed25519; p=o8owHm5pS4elBpxcmkA1v+gS8gI9E/u3fHC3LSqiacE="
```

This grants ownership of the `io.nameintel.*` namespace for all future publishes. The private key is required for any subsequent `mcp-publisher publish` — keep it safe (consider moving to Secrets Manager).

## To publish a new version

```bash
cd /path/to/server.json
# Bump version in server.json, then:
PRIV=$(openssl pkey -in /Users/toddmerrill/.nameintel/mcp-publisher-key.pem -noout -text \
  | grep -A3 "priv:" | tail -n +2 | tr -d ' :\n')
mcp-publisher login dns --domain=nameintel.io --private-key="$PRIV"
mcp-publisher publish
```

## Future room

We own the `io.nameintel.*` namespace. Future related servers could publish as:
- `io.nameintel/forge` — Phase 2 name generator
- `io.nameintel/monitor` — Phase 3 trademark monitoring
- etc.

The same Ed25519 key authorizes all of them.
