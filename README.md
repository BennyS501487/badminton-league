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

Keep the GitHub repository as the source of truth once Cloudflare is connected; update both `SCORES.md` and `public/index.html`.

## Current edition — Week 9 (corrected)

- Singles: Chris 3–0, Ben Hull 2–1, Dale 1–2, Benny 0–3.
- Doubles: Benny + Chris beat Ben Hull + Dale; Benny + Dale beat Ben Hull + Chris; Chris + Dale beat Benny + Ben Hull.
- Week 9 doubles player records: Benny, Chris and Dale 2–1; Ben Hull 0–3.
- Complete cumulative records are recomputed in `SCORES.md`.

To publish this update, upload/commit the **contents** of this repository to `main` (replace `public/index.html` and `SCORES.md` and keep `wrangler.jsonc` at the root). Cloudflare Workers Builds will deploy the commit automatically if already connected.
