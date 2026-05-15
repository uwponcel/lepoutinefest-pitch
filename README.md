# LePoutineFest — Pitch Mockup

Single-page editorial mockup for **LePoutineFest et Ramen T Fest** (1000 Bd Lachapelle, Saint-Jérôme). Built as a sales asset to send to Juliette ahead of signing.

## Stack

- Single `index.html` — self-contained
- React 18 + Babel standalone via CDN
- Tailwind CSS via CDN
- No build step

Everything (data, components, styles, animations) lives inline. Edit `index.html`, refresh browser, done.

## Local preview

```bash
npm install
npm run dev
```

Opens at `http://localhost:5173`. Uses the `serve` package.

Alternative: open `index.html` directly in any browser. CDN scripts work over `file://`.

## Deploy — Railway

This project is set up to deploy on Railway as a static site served via the `serve` npm package, bound to `$PORT`.

### Steps

1. Push this repo to GitHub (private or public, doesn't matter).
2. Railway dashboard → **New Project** → **Deploy from GitHub repo** → pick this repo.
3. Railway auto-detects Node via `package.json` + `nixpacks.toml`:
   - Install: `npm install`
   - Start: `npm start` (runs `serve . -l tcp://0.0.0.0:$PORT --single`)
4. Railway assigns a public URL like `lepoutinefest-pitch.up.railway.app` once the deploy is green.
5. Optional: Settings → Domains → add custom domain (e.g. `pitch.lepoutinefest.ca` via Cloudflare CNAME).

### How it works

- No build step. `index.html` is the entire site, loads React + Tailwind + Babel from CDN at runtime.
- `serve --single` ensures SPA-style fallback (all routes serve index.html).
- `$PORT` env var is set by Railway and consumed by the start script.

### Re-deploy

Push to the connected GitHub branch → Railway auto-redeploys via webhook. If a deploy fails on snapshot/clone (rare), trigger a manual redeploy from the Railway UI or push an empty commit:

```bash
git commit --allow-empty -m "Trigger redeploy"
git push
```

## What's in the design

- **Hero** — Stacked POUTINE / RAMEN graffiti display, neon glow, letter stagger entrance
- **Hairline** — Scroll-triggered neon divider between hero and sticky bar
- **Sticky bar** — Address / hours / phone in mono caps
- **Histoire** — Food truck → restaurant story, graffiti-framed photo placeholder
- **Menu** — 3 tabs (Poutines / Ramens / Subs), click any row to expand photo + ingredients
- **Galerie** — Asymmetric grid with parallax on feature image
- **Pourquoi** — 4.6 ★ / Address / Vegan+GF stat slabs
- **Reviews** — Real Google review excerpts, oversized italic display quotes
- **Visite** — Custom SVG fake-map with neon pin + hours grid
- **Footer** — Graffiti wordmark, social icons, Nord Studio credit

## Brand tokens

| Token | Value |
|---|---|
| Background | `#0A0A0A` (near-black) |
| Neon accent | `#A8FF35` (graffiti green) |
| Off-white text | `#F5F5F0` |
| Muted gray | `#9A9A92` |
| Display font | Anton (Google Fonts) |
| Body font | Inter |
| Marker font | Permanent Marker |
| Mono font | JetBrains Mono |

## Customization checklist before sending

- [ ] Real photos in place of striped placeholders (search `data-label` to find them)
- [ ] Real phone number replaces `450 000 0000`
- [ ] Real email replaces `bonjour@lepoutinefest.ca`
- [ ] Confirm hours grid matches actual operating hours
- [ ] Confirm menu items + prices still accurate
- [ ] Update Google review excerpts if new ones come in

## Credits

Site by Nord Studio · [nordstudio.io](https://nordstudio.io)
