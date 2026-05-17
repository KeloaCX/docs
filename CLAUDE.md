# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The Keloa user documentation site, built on [Mintlify](https://mintlify.com) and published at **docs.keloa.ai**. Content is end-user focused — not API/technical reference. Pages are MDX files with YAML frontmatter; navigation and theming live in `docs.json`.

**`AGENTS.md` is the authoritative contributor brief.** Read it before editing — it holds the exact terminology, style rules, content boundaries, and source-of-truth file list. The notes below are a summary, not a replacement.

## Commands

```bash
npm i -g mint        # install the Mintlify CLI (one-time)
mint dev             # local preview at http://localhost:3000
mint broken-links    # validate internal links — run before committing
```

There is no build, lint, or test step. Pushes to `main` auto-deploy via the Mintlify GitHub app.

## Structure

- A page's location in the sidebar is set by `docs.json` → `navigation.tabs`, **not** by the filesystem. Adding a new `.mdx` file does nothing until you register it in `docs.json`.
- Top-level `.mdx` files: `index`, `quickstart`, `onboarding`, `concepts`. Everything else lives in topic folders (`inbox/`, `agents/`, `knowledge/`, `flows/`, `channels/`, `contacts/`, `analytics/`, `settings/`, `developers/`, `billing/`, `account/`, `resources/`).
- Internal links are root-relative: `[Web widget](/channels/web-widget)` — never the full `https://docs.keloa.ai/...` URL.

## Content rules that matter

- **Document only shipped features.** Roadmap features need the roadmap callout pattern from `AGENTS.md` and a cross-link to `https://keloa.ai/roadmap`. Do not invent plausible-sounding controls (SSO steps, IP allowlists, quotas) that have no code path.
- **Hard numbers come from `keloacx-app`, never invention** — plan caps from `config/billing.php`, gate logic from `app/Services/Paywall.php`, what's wired from `routes/*.php` and `app/Http/Controllers/**`. The canonical reconciliation is `keloacx-app/docs/audits/2026-05-07-content-cross-reference.md`.
- **Terminology is fixed** and must match the product UI: *workspace*, *AI agent*, *channel*, *integration*, *knowledge source*, *reply* (say "credits" only in `billing/*`), *operator/teammate* for humans, *contact* for end customers, *conversation*, *flow*, *macro*. See `AGENTS.md` for the full list and the wrong words to avoid.
- **Channels vs. integrations vs. knowledge sources** are distinct concepts that are easy to conflate — Shopify appears in all three. `AGENTS.md` and `concepts.mdx` define each precisely.

## Style

Active voice, second person, sentence-case headings. Bold for UI elements (`Click **Save**`), `code` for endpoints/files/scopes. Use Mintlify components — `<Note>`/`<Tip>`/`<Info>`/`<Warning>` for callouts, `<Steps>`/`<Step>` for setup, `<CardGroup>`/`<Card>` for nav grids. Numbers use comma grouping (`1,500`).
