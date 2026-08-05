# genial-labs-site

Source for [genial-labs.com](https://genial-labs.com) — the consulting site for Ravi Kalia.

Plain static HTML. No build step, no framework, no JavaScript, and no external network
requests. Deployed to GitHub Pages by `.github/workflows/static.yml` on every push to `main`.

```
index.html    the entire site (single page)
style.css     hand-written stylesheet
assets/       logo + favicon
CNAME         genial-labs.com
```

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

---

## Integrations — all wired

### ✅ Booking link — done

The "Book a call" buttons (3 occurrences) point at the Google Calendar appointment schedule
"Intro call — Genial Labs":

```
https://calendar.app.google/dGPzDkEEuXYKe1zj6
```

If you ever rebuild that schedule in Google Calendar the short link changes, so update all
three occurrences together.

### ✅ Contact form — done, but send one test submission

The form posts to `https://formspree.io/f/xeajqklq`, delivering to `ravi@genial-labs.com`.

**This was not verified end-to-end.** A GET request cannot tell a valid Formspree form ID from
an invalid one, and submitting a test POST would have sent you a real message, so that step was
left to you. Formspree also requires the owner to confirm the first submission on a new form
before it starts delivering. So: **submit the form once yourself** on the live site, confirm the
email that arrives, and it is done. Until then, treat delivery as unproven.

The `mailto:` fallback below the form works regardless.

### ✅ Newsletter — done

Posts to `https://buttondown.com/api/emails/embed-subscribe/kalia`
([buttondown.com/kalia](https://buttondown.com/kalia)).

The older `buttondown.email` host still works but costs an extra redirect, so the form uses
`buttondown.com` directly. It is a plain HTML `<form>` — no script tag and no iframe — so there
is nothing to maintain and nothing that slows the page down.

---

## What I still need from you

None of these break the site — the page is honest and complete without them — but each
materially improves it. They are tracked here rather than as comments in `index.html`, because
HTML comments are readable in view-source and these are internal notes. Roughly in order of
impact:

1. **Client engagements.** Two card slots are scaffolded and commented out at the end of the
   Selected Work section. Everything currently on the site is public or personal work; nothing
   shows that someone *paid* you for this. For each engagement I need problem, approach, stack,
   outcome (with a number if you have one), and a link if anything is public. Tell me what is
   NDA-safe — "a Series B biotech" reads fine if you cannot name them.

2. **Social Finance — needs detail for a proper card.** Currently a one-line entry in the work
   history: "AI engineering consulting, 2025". This is your only named consulting client on the
   site, so it is worth a full work card. Send me problem, approach, stack and outcome, plus
   which Social Finance entity it is (there are UK and US organisations of that name) — and
   confirm you can name them publicly, since this is client work rather than employment.

3. **Ritual.co job title.** The card and work-history entry say "machine learning and data
   engineering", which is a description of the work taken from a colleague's recommendation on
   your LinkedIn, not your actual title — the profile has no experience entry for Ritual. Send
   me the real title and I will swap it in.

4. **Sargassum detector outcome.** The card describes what was built but claims no result, which
   is the honest default. If you have detection performance, or it was used operationally, that
   turns a project into a case study.

5. **Open-source scope.** The site claims exactly what I could verify: three merged commits to
   PyTorch Geometric and one to einops. Your GitHub profile also shows forks of `mlx`,
   `mlx-graphs` and `pytorch-frame` with no upstream commits, so those are deliberately not
   claimed — a technical buyer checks this in under a minute, and an overclaim here would cost
   more than the claim is worth. If you have contributions under another account or email, send
   them and I will widen it.

6. **Engagement model.** Typical length, advisory vs. build split, availability, and whether to
   publish a rate. Being concrete filters bad-fit enquiries before they reach your inbox.

7. **Years of experience.** I left a number out of the hero because I could not verify one. Give
   me a start year and I will add it.

8. **A proper `og:image`.** Currently pointing at `assets/brain_logo.png` (379×262) so link
   previews are not broken. A purpose-made 1200×630 image at `assets/og-image.png` would look
   considerably better when the site is shared.

---

## Notes

- **The blog has no RSS feed.** The Writing section hardcodes the eight most recent posts, so it
  will go stale. `https://project-delphi.github.io/ml-blog/index.xml` currently 404s — adding
  `feed: true` to the listing options in `_quarto.yml` in the `ml-blog` repo would enable one.
  Longer term, moving the blog to `genial-labs.com/writing` would consolidate the two domains.
- **This rewrite replaces the `content-update` copy, which was already live.** That content was
  merged as PR #31 and deployed on 2025-11-24: it described Genial Labs as having "a talented
  team of AI engineers and researchers" and listed twelve buzzwords under Expertise. Both work
  against the positioning here, and both are gone. If you ever restore from an older commit, do
  not bring those two back.
- **Favicon.** `assets/favicon.png` is 96×66 — non-square, because the `sips -Z 96` command
  previously documented here preserves aspect ratio. Worth re-exporting square at some point:
  `sips -z 96 96 ./assets/brain_logo.png --out ./assets/favicon.png` (lowercase `-z` takes
  height then width).
