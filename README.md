# cfd-website

**This is an independent, unsolicited redesign concept — not the official
website of Centennial Family Dentistry, and not affiliated with, endorsed by,
or produced on behalf of the practice.**

It's a pitch: a from-scratch reimagining of the practice's public site
(Snohomish, WA), built by [Delicious LLC](https://wearedelicious.com) to show
what a modern, mobile-first version of the same real content could look like.
Every fact used on the site (prices, hours, names, services) is sourced
verbatim from the practice's own live site as it existed on 2026-07-22, with
citations — see `brand/products.md`. Nothing about the practice is invented.

Will deploy to: `https://deliciousllc.github.io/cfd-website/` (not yet live).

## Layout

```
cfd-website/
├── CLAUDE.md          session instructions for AI coding tools working in this repo
├── brand/             brand system — facts, voice, and visual tokens extracted
│                       from the practice's live site (start at _START_HERE.md)
├── site/              the Astro site itself
└── architecture/      specs, plans, and reviews behind this project
```

## Running the site locally

Once `site/` exists:

```bash
cd site
npm install
npm run dev
```

The site is a static Astro project deployed to GitHub Pages via GitHub
Actions on push to `main`. It's built under a `/cfd-website` base path, so
local links and assets should resolve the same way they will once deployed.

## Why this exists

The practice's current site has real strengths — three named doctors,
unusual pricing transparency, and differentiating services — buried under a
flat, ~20-item navigation with no clear call to action. This repo is a
concept redesign meant to make that gap, and the fix, obvious.
