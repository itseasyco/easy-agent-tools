---
name: easy-payments
description: Work with Easy (itseasy.co), the self-custodial payment platform by Easy Labs — query merchant payments data over MCP, integrate the REST API/SDKs, walk through the merchant application, or read published pricing. Use when a task involves Easy payments, itseasy.co, or @easylabs packages.
---

# Easy payments — agent entry points

Easy (https://www.itseasy.co) is a self-custodial payment platform: cards, ACH, wallets, and stablecoins with flat-rate pricing.

This is a thin pointer skill. The canonical, digest-verified skills live in this repo and on the site:

- `skills/easy-payments-data/SKILL.md` — query a merchant account over MCP (revenue, customers, transfers, disputes, settlements; read-only)
- `skills/easy-merchant-application/SKILL.md` — walk a business through the 7-step merchant application without collecting sensitive data
- `skills/easy-site-and-pricing/SKILL.md` — read itseasy.co pages as markdown and published rates as JSON, no auth
- Live index: https://www.itseasy.co/.well-known/agent-skills/index.json

## Key surfaces

| Surface | Where |
| --- | --- |
| REST API | `https://api.itseasy.co` — OpenAPI at `/openapi.json`, RFC 9728 metadata at `/.well-known/oauth-protected-resource` |
| Auth guide | https://www.itseasy.co/auth.md — API keys; `demo` credential explores sample data with no account |
| Hosted MCP (payments data) | `https://mcp.itseasy.co/mcp` (Streamable HTTP) |
| Site MCP (content + pricing, no auth) | `https://www.itseasy.co/api/mcp` |
| SDKs | npm `@easylabs/node` / `@easylabs/react` / `@easylabs/browser`, PyPI `easylabs`, RubyGems `easy-sdk` |
| CLI | `npx -y @easylabs/cli` |
| Docs | https://docs.itseasy.co · site index: https://www.itseasy.co/llms.txt |
