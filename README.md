# Easy agent tools

Skills, agent guidance, and plugin manifests for working with [Easy](https://www.itseasy.co) — the self-custodial payment platform by Easy Labs, Inc. (cards, ACH, wallets, and stablecoins with zero stablecoin fees).

Everything here is a thin, versioned pointer to Easy's live agent surfaces. The canonical, digest-verified copies of the skills are served by the site itself at `https://www.itseasy.co/.well-known/agent-skills/index.json`.

## Skills

| Skill | What it does |
| --- | --- |
| [`easy-payments-data`](skills/easy-payments-data/SKILL.md) | Query a merchant account over MCP: revenue summaries, customers, transfers, disputes, settlements. Read-only. |
| [`easy-merchant-application`](skills/easy-merchant-application/SKILL.md) | Walk a business through the 7-step merchant application without ever collecting sensitive data. |
| [`easy-site-and-pricing`](skills/easy-site-and-pricing/SKILL.md) | Read itseasy.co pages as markdown and published processing rates as JSON — no auth. |

Install with [skills.sh](https://skills.sh):

```bash
npx skills add itseasyco/easy-agent-tools
```

Or point any SKILL.md-aware tool at the raw files above.

## Other Easy agent surfaces

| Surface | Where |
| --- | --- |
| Hosted MCP (payments data) | `https://mcp.itseasy.co/mcp` — Streamable HTTP; no credential = demo data |
| Local MCP | `npx -y @easylabs/mcp-server` |
| CLI | `npx @easylabs/cli` |
| Site MCP (content + pricing, no auth) | `https://www.itseasy.co/api/mcp` |
| REST API | `https://api.itseasy.co` — OpenAPI at `/openapi.json` |
| Machine-readable site | `https://www.itseasy.co/llms.txt`; append `.md` to any page URL |
| Auth guide for agents | `https://www.itseasy.co/auth.md` |

## Contents

- `skills/` — SKILL.md files (frontmatter `name` + `description`, skills.sh-compatible)
- `AGENTS.md` — guidance for coding agents integrating with Easy
- `plugin.json` — agent-plugins manifest

## License

MIT — see [LICENSE](LICENSE). Pricing and product facts referenced in the skills are descriptive of Easy's live, published rates; always verify via `get_pricing_rates` or `https://www.itseasy.co/pricing.md`.
