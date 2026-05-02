# `landing/`

Static landing page + privacy policy for **Slop Bin**. Deployed to **Vercel** (free tier).

## Structure

| Path | Purpose |
|------|---------|
| `index.html` | Marketing landing page. |
| `privacy.html` | Privacy policy (Chrome Web Store requires a public HTTPS URL). |
| `styles.css` | Shared palette/typography (mirrors the extension popup). |
| `assets/` | Reused art from the extension (`truck.png`, `trashbag.png`, `bin.png`). |
| `vercel.json` | Clean URLs (`/privacy` → `privacy.html`) + minimal security headers. |

## Local preview

Open the files in a browser, or serve the folder:

```bash
npx serve landing
```

## Deploy (Vercel)

From the repo root:

```bash
vercel --cwd landing
```

The first run prompts for project + scope; later runs reuse the link. After deploy:

1. **Privacy URL** — copy the live `/privacy` URL into the **Chrome Web Store → Privacy policy** field.
2. **Add-to-Chrome CTA** — once Chrome Web Store listing is live, swap the placeholder href on the **Add to Chrome** buttons in `index.html`.
3. **Canonical / social URLs** — find/replace `https://slop-bin.vercel.app` in `index.html` and `privacy.html` with your real Vercel domain (or custom domain). Same for the JSON-LD blocks.

This folder has no build step — Vercel serves it as-is.

## SEO checklist

- `<title>` and meta `description` on both pages.
- Open Graph + Twitter cards (with `og:image` pointing to `truck.png`; replace with a proper 1200×630 social image when designed).
- Canonical link tags (placeholder domain — swap on deploy).
- JSON-LD: `SoftwareApplication` + `FAQPage` on the home page.
- Single `<h1>` per page, semantic section structure.
