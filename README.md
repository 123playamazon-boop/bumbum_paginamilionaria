# bumbum_paginamilionaria

Static landing page for the BumBum Cream affiliate funnel — Brazilian skincare advertorial deployed for native ad traffic (Newsbreak, Taboola, Outbrain).

## Stack

- 100% static HTML / CSS / vanilla JS
- No build step
- Vercel hosting with edge caching
- RedTrack click ID forwarding to Stripe checkout

## Files

- `index.html` — the landing page (entry point)
- `milionaria.html` — alias of index.html
- `img/` — all referenced assets (images, MP4 videos, badges)
- `vercel.json` — Vercel config (cache headers, security headers, clean URLs)

## Deploy

This repo is wired for Vercel. Pushing to `main` triggers automatic redeploy.

```bash
# Local preview (serves on http://localhost:3000)
npx serve .
```

## Tracking

The page reads `?rtkcid=...` from the URL on landing, persists it in `sessionStorage`, and forwards it to all `buy.stripe.com` links so RedTrack attributes the conversion correctly.

## Compliance notes

- FDA disclaimer present in footer (cosmetic, not medical claims)
- Composite testimonial disclosure included
- Advertorial label in footer
- No "FDA Approved" claim
- 60-day money-back guarantee at every CTA

## Updating the LP

Edit `index.html` (the master) and copy to `milionaria.html` to keep them in sync. Both files should always be byte-identical:

```bash
cp index.html milionaria.html
git add . && git commit -m "Update LP" && git push
```

Vercel rebuilds on push.

## Backups

Working backups (5 versions in chronological order) live in the parent `Bumbum/` folder, NOT in this repo. They are intentionally excluded via `.gitignore`.
