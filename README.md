# genial-labs-site

Source for [genial-labs.com](https://genial-labs.com) — the consulting site for Ravi Kalia.

Plain static HTML. No build step and no framework. One page, one stylesheet.

```
index.html    the entire site (single page)
style.css     hand-written stylesheet
assets/       logo, favicon, Open Graph card
robots.txt    crawler policy
sitemap.xml   one URL, the homepage
CNAME         genial-labs.com
NOTES.md      working notes — not deployed
```

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deployment

`.github/workflows/static.yml` runs on every push to `main`. It copies the site files
into `_site/` and publishes that directory to GitHub Pages — deliberately **not** the
repository root, so `README.md`, `NOTES.md` and `.gitignore` are never served. If you add
a new top-level file that belongs on the site, add it to the `Assemble site` step too.

## External services

| Thing | Where |
|---|---|
| Booking link | Google Calendar appointment schedule "Intro call — Genial Labs" |
| Contact form | Formspree form `xeajqklq` → ravi@genial-labs.com |
| Newsletter | [buttondown.com/kalia](https://buttondown.com/kalia) |
| Analytics | Plausible, per-site script `/js/pa-r79QP5jHw7O4InoilgaQ0.js` (no `data-domain` — the domain is baked into the file) |

The booking URL appears four times (header, hero, mid-page CTA, contact section) with
different `utm_content` values. If you rebuild the appointment schedule in Google Calendar
the short link changes — update all four together.

See `NOTES.md` for outstanding content work.
