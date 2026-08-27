---
name: easy-merchant-application
description: Walk a business through applying for an Easy (itseasy.co) merchant account — the 7 steps, what to gather, and the sensitive-data boundary.
---

# Easy merchant application guide

## When to use

Use this skill when someone wants to accept payments with Easy and asks "how do I sign up?", "what do I need to apply?", or "what's step 4 about?". The application takes ~10 minutes when everything is gathered up front.

## How to work

1. Call `merchant_application_checklist` on `https://mcp.itseasy.co/mcp` (works with no credentials) for the full 7-step preparation list.
2. Call `explain_application_step` with a step number (1–7) to explain any step in plain English: business details, business type, tax details, owners, merchant settings, processing volume, review & terms.
3. Send the user to https://app.itseasy.co to complete the application.

## Hard boundary

NEVER collect SSNs, EINs, or bank credentials in conversation. Those fields are entered only in the secure hosted form, which tokenizes them in the browser. Your job is preparation and explanation, not data collection. Consent (step 7) must be the human clicking, not you.
