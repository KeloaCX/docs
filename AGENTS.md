# Documentation project instructions

## About this project

- This is the Keloa documentation site, built on [Mintlify](https://mintlify.com).
- Pages are MDX files with YAML frontmatter.
- Configuration lives in `docs.json`.
- Run `mint dev` to preview locally.
- Run `mint broken-links` to check links.

## Terminology

Use these Keloa-specific terms exactly. They are wired into the product UI and the marketing site, so docs need to match.

- **Workspace** — the tenant container. Not "project", not "team", not "org".
- **AI agent** — an LLM-backed responder configured per workspace. Not "bot", not "assistant", not "chatbot".
- **Channels** — the places messages come in. The two live channels are the **web widget** and **email**. WhatsApp, Instagram, Messenger, and Shopify-as-channel are on the roadmap.
- **Integrations** — third-party data systems the AI calls or syncs from (Shopify is the canonical live integration; custom HTTP endpoints also count).
- **Knowledge sources** — the four ingestable types: **website crawl**, **text snippet**, **file upload**, **Q&A pairs**. Shopify is a **fifth knowledge source** in the knowledge context only — separate from the Shopify integration that exposes order/product/tracking tools.
- **Replies** — the user-facing word for what the AI sends. Use this in product copy.
- **Credits** — the internal billing unit. One credit ≈ one AI round-trip. Use "credits" in `billing/*` docs only; everywhere else say "replies".
- **Operator** or **teammate** — a human user of Keloa. Never "user" for humans (that word is reserved for Laravel/internal context).
- **Contact** — the end customer the workspace is talking to. Not "customer" in product context (use "customer" only in marketing copy).
- **Conversation** — the threaded record of messages with one contact on one channel. Not "thread", not "ticket", not "case".
- **Flow** — a deterministic automation built in the flow builder. Not "workflow", not "automation rule".
- **Macro** — a saved reply template a teammate can paste. Not "canned response".

## Style preferences

- Active voice, second person ("you").
- Sentence case in headings — only the first word and proper nouns capitalised.
- One idea per sentence; lead with the goal.
- Bold for UI elements: "Click **Save**", "open **Settings → Security**".
- `code` for endpoints, file names, env vars, scopes (e.g. `read_orders`).
- Use `<Note>`, `<Tip>`, `<Info>`, `<Warning>` Mintlify components rather than bold-italic emphasis for callouts.
- Use `<Steps>` / `<Step>` for sequential setup, `<CardGroup>` / `<Card>` for navigational grids.
- Numbers: `1,500` (comma) for English; never `1 500` (thin-space) — keep one canonical form.

## Content boundaries

**Document features that exist in the app today.** If a feature lives in `keloacx-app/config/billing.php` with a non-zero cap and has shipping code in `app/`, document it normally.

**For roadmap features**, include a roadmap callout at the top of the page (or section) and cross-link to `https://keloa.ai/roadmap`. Today's roadmap items, per the cross-reference audit:

- **Channels:** WhatsApp Business, Instagram, Messenger, Shopify-as-channel (storefront chat).
- **Integrations:** HubSpot, Salesforce, Mollie, Notion, Zapier, WooCommerce, Slack as customer-facing.
- **Auth:** SSO (SAML/OIDC), Google OAuth login.
- **Developer surface:** public REST API, public webhooks API.

Use this exact pattern for roadmap pages:

```mdx
<Tip>
Track availability on the [Keloa roadmap](https://keloa.ai/roadmap).
</Tip>

<Note>
**Coming soon.** [feature] is not yet shipped. The flow below describes the planned setup.
</Note>
```

**Do not document unshipped features without that banner.** Specifically, do not invent SSO setup steps, IP allowlists, configurable session timeouts, per-agent quotas, or other plausible-sounding controls that have no code path.

## Cross-references

- Marketing site: `https://keloa.ai`
- Roadmap: `https://keloa.ai/roadmap`
- App: `https://app.keloa.ai`
- Docs (this site): `https://docs.keloa.ai`
- Legal sub-processors page (note hyphen): `https://keloa.ai/legal/sub-processors`

Internal doc links use root-relative paths: `[Web widget](/channels/web-widget)`, never `https://docs.keloa.ai/channels/web-widget`.

## Source-of-truth files in `keloacx-app`

When a doc needs hard numbers, read these files (do not invent values):

- `config/billing.php` — every plan cap (credits, agents, seats, channels, knowledge MB, pages, integrations, flows, daily ceilings).
- `app/Services/Paywall.php` — gate logic for `*.use` and `*.create` permissions.
- `routes/*.php` and `app/Http/Controllers/**` — what's actually wired and shipping.

## When in doubt

Match the cross-reference matrix at `keloacx-app/docs/audits/2026-05-07-content-cross-reference.md` — it is the canonical reconciliation between app, website, and docs.
