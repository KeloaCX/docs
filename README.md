# Keloa docs

Source for the Keloa user documentation, hosted on [Mintlify](https://mintlify.com).
Published at **[docs.keloa.ai](https://docs.keloa.ai)**.

Keloa is a multi-tenant AI-first omnichannel customer engagement platform:
a unified inbox across webchat, email, WhatsApp, Instagram, Messenger, and
Shopify, with a per-workspace AI agent grounded in your own knowledge base.

## Structure

```
index.mdx           — landing page
quickstart.mdx      — 15-minute setup
onboarding.mdx      — walkthrough of first-run wizard
concepts.mdx        — core concepts

inbox/              — inbox, replying, macros, assignments, resolving
agents/             — creating, prompting, tools, testing AI agents
knowledge/          — website crawl, files, snippets, Q&A pairs
flows/              — triggers, conditions, messages/actions, handoff, publishing
channels/           — web widget, email, WhatsApp, Instagram, Messenger, Shopify
contacts/           — contact and company profiles
analytics/          — metrics and breakdowns
settings/           — workspace, members, assignment rules, widget, tools, data & privacy, security
billing/            — plans, usage & credits, managing subscription
account/            — personal profile, password & 2FA, invitations
resources/          — FAQ, troubleshooting, glossary
```

Navigation lives in `docs.json` under `navigation.tabs`.

## Local preview

```bash
npm i -g mint
mint dev
```

Then open <http://localhost:3000>.

## Contributing

- Keep docs end-user focused — not technical/API docs.
- Prefer task-oriented pages ("How to X") over feature lists.
- Use short paragraphs and tables over prose where possible.
- Match existing voice: direct, friendly, pragmatic.

## Logo and branding

Logo files live in `logo/` (wordmark, light and inverse) and `favicon.svg` (mark only).
Channel icons are in `images/channels/`. All sourced from `keloacx-website/public/assets`.

## Publishing

Changes pushed to `main` auto-deploy via the Mintlify GitHub app.
