# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static site for **Conduta** — a social deduction game by OwnerSheep Studio. The site's primary goal is converting visitors to join the Discord community at `https://discord.gg/mwp6Z8s8ux`.

Deployed at **ownersheep.com.br** via Vercel. GitHub: `NikolasRaposo/OwnerSheep`.

## Deploy

```bash
# Deploy to production
npx vercel --prod --yes

# Push + deploy in one step
git push && npx vercel --prod --yes
```

Vercel is configured via `vercel.json` with `outputDirectory: public`. No build step — pure static HTML. Every push to `master` triggers a new deploy automatically via the connected GitHub repo.

## Structure

```
public/
  conduta/
    index.html        → ownersheep.com.br/conduta       (main landing page)
    terms/index.html  → ownersheep.com.br/conduta/terms (terms & conditions)
    policy/index.html → ownersheep.com.br/conduta/policy (privacy policy)
```

The root-level `conduta.html`, `terms.html`, and `privacy.html` are the original source files — the canonical versions live under `public/`.

## Design System

All pages share the same CSS variables and typography — no external CSS files:

| Variable | Value | Usage |
|----------|-------|-------|
| `--bg` | `#1a1812` | Page background |
| `--bg3` | `#2a2620` | Card backgrounds |
| `--gold` | `#c9a84c` | Accents, CTAs, highlights |
| `--cream` | `#e8e0d0` | Primary text |
| `--muted` | `#9a9080` | Secondary text |
| `--border` | `rgba(201,168,76,0.18)` | Subtle dividers |

Fonts (Google Fonts): `Cormorant SC` (headings/brand), `Cormorant Garamond` (display/legal titles), `Jost` (body/UI).

## Conversion Rules

- Every CTA button must link to `https://discord.gg/mwp6Z8s8ux` with `target="_blank" rel="noopener noreferrer"`
- Primary CTAs use `.btn.btn-gold` with the Discord SVG icon inline
- The Discord icon SVG path is reused across all CTA buttons — copy from an existing button rather than recreating
- CTAs appear in: hero, community-power section end, participate section end, roadmap box, final CTA section, footer nav
