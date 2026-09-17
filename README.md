# pSEO Engine — remote MCP server quick reference (no account needed to try)

Programmatic SEO as callable tools: research a query space, generate landing pages, audit for answer engines, publish to your own domain, track rankings.

**Endpoint (Streamable HTTP):** `https://pseo.quantumcx.net/api/agent/mcp`
**Registry:** `net.quantumcx/pseo-engine` (Official MCP Registry)
**Connector score:** https://glama.ai/mcp/connectors/net.quantumcx/pseo-engine

## Connect in one line (Claude Code)

```bash
claude mcp add --transport http pseo https://pseo.quantumcx.net/api/agent/mcp
```

## Verify anonymously

`initialize` and `tools/list` need no key:

```bash
curl -s -X POST https://pseo.quantumcx.net/api/agent/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

## Rules

- Call `seo_project_list` first — every tool needs a projectId; creation is free.
- ASYNCHRONOUS tools return a jobId; poll `seo_job_status` to COMPLETED.
- Costs: page = 2 actions, research run = 50 flat, audit = 1. Reads free.
- BYOK: AI tokens run on your own key (a free Gemini key works). No markup.
- Writes need a prepaid key — packs from $499, never expire, per-key daily cap.

Full walkthrough: https://gist.github.com/quantumcxai-ship-it/4e242228c61fb1a6bcaa8693547af5c3
Site: https://quantumcx.net · Pricing: https://quantumcx.net/pricing
