# AGENTS.md — integrating with Easy

Guidance for AI agents and the developers pointing them at Easy (itseasy.co), a self-custodial payment platform: cards, ACH, wallets, and stablecoins (stablecoin processing is free).

## Fastest paths

- **Answer product/pricing questions**: fetch `https://www.itseasy.co/llms.txt`, or append `.md` to any page URL (`/pricing.md` has the full rate table). No auth. There is also an unauthenticated MCP server at `https://www.itseasy.co/api/mcp` with `list_pages`, `get_page`, and `get_pricing_rates`.
- **Query a merchant account**: MCP at `https://mcp.itseasy.co/mcp` (Streamable HTTP). Auth with `x-easy-api-key: sk_...`. No key — or the literal key `demo` — serves deterministic sample data, so you can evaluate every tool without an account.
- **Call the REST API**: `https://api.itseasy.co`, OpenAPI at `https://api.itseasy.co/openapi.json`. Auth header `x-easy-api-key`. Key prefixes route: `sk_live_`/`pk_live_` → production, `sk_test_`/`pk_test_` → sandbox.
- **Natural-language site search**: `POST https://www.itseasy.co/ask` with `{"query": "..."}` (NLWeb-style, schema.org results).

## Conventions that matter

- **Idempotency**: `POST /v1/api/transfer*`, `/v1/api/authorizations`, and `/v1/api/invoices` accept an `Idempotency-Key` header (or the equivalent `idempotency_id` / `idempotency_key` body field). Send a fresh UUID per logical operation and reuse it on retries.
- **Rate limits**: every response carries IETF `RateLimit-*` headers. Self-throttle on `RateLimit-Remaining`; honor `Retry-After` on 429s.
- **Errors**: non-2xx responses are a stable envelope `{ "success": false, "error": { "code", "message" } }`. Branch on `error.code`.
- **Money**: amounts are integer cents, USD unless stated.

## Hard boundaries

- Never collect SSNs, EINs, bank credentials, or card numbers in conversation. Sensitive fields are entered only in Easy's secure hosted forms, which tokenize in the browser.
- The MCP data tools are read-only; nothing in this repo moves money.
- Consent steps (terms acceptance, application submission) must be performed by the human, not the agent.

## Credentials

See `https://www.itseasy.co/auth.md` for the full agent-facing auth walkthrough (how to get keys, demo mode, revocation). Keys are self-serve at https://app.itseasy.co.

## Working on this repo

Skills in `skills/` mirror the digest-verified copies served at `https://www.itseasy.co/.well-known/agent-skills/index.json` — treat the site as canonical and keep the two in sync when editing. Frontmatter must keep `name` and `description`, and every skill body needs a "## When to use" section.
