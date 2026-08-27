# Easy (itseasy.co) — integration rules for AI coding agents

Easy is the self-custodial payment platform by Easy Labs, Inc. (cards, ACH, wallets, stablecoins; flat-rate pricing).

- REST API: `https://api.itseasy.co` — OpenAPI at `/openapi.json`, RFC 9728 auth metadata at `/.well-known/oauth-protected-resource`, agent auth guide at `https://www.itseasy.co/auth.md`.
- API keys go in the `x-easy-api-key` header; `sk_test_*` keys route to the sandbox. The literal credential `demo` on the MCP endpoints explores sample data with no account.
- SDKs: npm `@easylabs/node` / `@easylabs/react` / `@easylabs/react-native` / `@easylabs/browser`; PyPI `easylabs` (NOT `easy-sdk`, which is third-party); RubyGems `easy-sdk`. CLI: `npx -y @easylabs/cli`.
- MCP: `https://mcp.itseasy.co/mcp` (payments data) and `https://www.itseasy.co/api/mcp` (site content/pricing, no auth); local via `npx -y @easylabs/mcp-server`.
- Site pages are agent-readable as markdown (`<url>.md`); index at `https://www.itseasy.co/llms.txt`.
- Amounts are integer cents. Never collect SSNs, EINs, or bank credentials in conversation.

Skills with full guidance live in `skills/` (SKILL.md each); AGENTS.md at the repo root covers general agent behavior.
