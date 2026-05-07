# wonminkim.com

Personal portfolio — Wonmin Kim · Data analyst at P&V Insurance, Brussels.

Cross-border data and product work, KR ↔ EU. Building [ARBITORIA](https://arbitoria.com) and [Salaire-Plus](https://salaire-plus.com).

**Live:** [wonminkim.com](https://wonminkim.com)

---

## Stack

Plain HTML/CSS, no build step. Vercel for deployment.

- `index.html` — main page (English)
- `styles.css` — shared stylesheet
- `projects/` — case studies (English)
  - `arbitoria.html`
  - `salaire-plus.html`
  - `insurance-analytics.html`
- `fr/` — French version
  - `fr/index.html`
  - `fr/projects/*.html`

Language toggle in header (EN · FR) on every page. SEO `hreflang` tags configured.

## Local preview

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Deployment

Pushed to `main` → Vercel auto-deploys.

---

© Wonmin Kim · 2026 · Brussels
