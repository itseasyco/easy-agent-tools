---
name: easy-payments-data
description: Query an Easy (itseasy.co) merchant account: revenue summaries, customer lookup, transfers, disputes, settlements. Read-only, over MCP.
---

# Easy payments data

## When to use

Use this skill when a user asks about their Easy merchant account: "how's revenue?", "find customer jane@…", "any open disputes?", "when was my last settlement?". Easy is a self-custodial payment platform (cards, ACH, wallets, stablecoins).

## How to connect

Remote MCP (Streamable HTTP): `https://mcp.itseasy.co/mcp`
- Auth header: `x-easy-api-key: sk_...` (live keys → production, test keys → sandbox)
- No credential, or the literal value `demo`, serves deterministic sample data — safe for demos and evaluation.

Local: `npx -y @easylabs/mcp-server` (set `EASY_API_KEY`, or `EASY_ENVIRONMENT=demo`).

## How to work

1. Prefer the workflow tools: `revenue_summary` (periods 7d/30d/90d/6m/12m/mtd, includes previous-period comparison) and `find_customer` (email/name search with recent activity).
2. Fall back to `list_transfers`, `list_disputes`, `list_settlements`, `list_customers`, `list_balance_transfers` and their `get_*` twins for specifics.
3. Read the `merchant://summary` resource for account context.
4. Amounts are integer cents, USD unless stated. All tools are read-only — nothing moves money.

## Boundaries

Never ask users for SSNs, EINs, or bank credentials. Demo data self-identifies (`demo_*` ids, @example.com emails).
