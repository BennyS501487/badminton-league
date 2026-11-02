# Badminton League

This repository hosts the league scoreboard on Cloudflare Workers.

## Structure
- `public/index.html` — complete static website (Overview, Standings, Head-to-Head, Weeks)
- `SCORES.md` — canonical week-by-week score ledger
- `wrangler.jsonc` — Cloudflare Worker configuration

## Continuous deployment

Connect this repository to **Cloudflare Workers Builds** (production branch: `main`).
- Worker name: `badminton-league` (must match `wrangler.jsonc`).
- Build command: leave blank (no compilation needed).
- Deploy command: `npx wrangler deploy`.
- Root directory: `/` (repository root).

A commit to `main` triggers the deploy. The public website is served from `public/index.html`.

## Updating the scores

1. Apply new results to the full match ledger in `SCORES.md`.
2. Recalculate standings and head-to-head from the underlying match data.
3. Update `public/index.html` and commit both files to `main`.

Do not use the old Week 8 HTML download as the live source after this repository is connected.
