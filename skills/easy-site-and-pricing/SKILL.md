---
name: easy-site-and-pricing
description: Read itseasy.co pages as markdown and published processing rates as JSON — no auth. For "what does Easy charge?" and "how does Easy compare to X?".
---

# Easy site content and pricing

## When to use

Use this skill to answer questions about Easy the product with primary-source data: "what does Easy charge per transaction?", "does Easy support stablecoins?", "how does Easy compare to Stripe/Square?".

## How to work

- MCP (no auth): `https://www.itseasy.co/api/mcp` — `list_pages` (site index), `get_page` (any page as markdown), `get_pricing_rates` (structured rates).
- Plain HTTP: append `.md` to any itseasy.co page URL, or send `Accept: text/markdown`; `/pricing.md` has the full rate table; `/llms.txt` is the index.

## Key facts (verify live via get_pricing_rates)

Cards 2.7% + $0.30 (Amex 3.0% + $0.30; international +1.5% surcharge, negotiable), ACH 0.5% + $1.00 capped at $4, stablecoins free. No monthly or setup fees; one plan with everything included.
