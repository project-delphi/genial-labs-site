# Working notes

Internal. Excluded from the deploy by the `Assemble site` step in
`.github/workflows/static.yml` — check that still holds before adding anything candid here.

---

## Blocked on content from Ravi

These are the slots the site is currently missing. Everything else has shipped.

### 1. A paying-client work card — highest impact

Every full card on the site is employment, academic or open-source work. Nothing says a
client hired Genial Labs. **Social Finance** (2025, AI engineering consulting) is the
obvious candidate and is currently only a one-line entry in the work history.

Needed: which entity (there are separate UK and US organisations of that name), problem,
approach, stack, outcome with a number if one exists, and confirmation that they can be
named publicly — this is client work rather than employment, so that is not automatic.
"A UK social-impact organisation" reads fine if they cannot be named.

Drop into the top of `.work-grid` in `index.html` using this shape:

```html
<article class="work-card">
    <h3>ENGAGEMENT TITLE</h3>
    <p class="card-meta">CLIENT OR SECTOR &middot; YEAR</p>
    <dl>
        <dt>Problem</dt>  <dd>WHAT THEY CAME TO YOU WITH</dd>
        <dt>Approach</dt> <dd>WHAT YOU BUILT</dd>
        <dt>Stack</dt>    <dd>TOOLS</dd>
        <dt>Outcome</dt>  <dd>RESULT, WITH A NUMBER IF YOU HAVE ONE</dd>
    </dl>
    <p class="links"><a href="URL">Writeup</a></p>
</article>
```

### 2. Testimonials

Nothing shipped, because there is nothing to quote yet. Two sentences from a former
client or manager, placed right after the mid-page CTA, is the single cheapest
conversion gain left on the page. One quote is enough to start.

Needed per quote: the words, name, role, company, and permission.

Markup and styling are not yet written — `.testimonial` does not exist in `style.css`.
Ask for it when the first quote arrives.

### 3. Availability and location

The About section says "a small number of engagements at a time" and nothing else. A
buyer self-qualifies on where you are, which timezones you work across, and whether you
have capacity this quarter. Needed: base city, working timezones, and a current capacity
line ("two slots from November") that you are willing to keep up to date.

### 4. Ritual.co job title

The card and the work-history entry both say "machine learning and data engineering".
That is a description of the work taken from a colleague's LinkedIn recommendation, not a
title — the profile has no experience entry for Ritual. Send the real title.

### 5. Do the offer names match how you sell?

`index.html` now names four engagements: evaluation & calibration audit, agent &
retrieval build, applied ML for scientific data, fractional ML lead. Durations are
stated, prices are not. If you pitch these differently on calls, the page should match
the pitch rather than the other way round.

### 6. Years of experience

Left out of the hero because there is no verified start year. Give one and it goes in.

### 7. Sargassum detector outcome

Now in the compact "Also" list rather than a full card, because it claims no result. If
there is detection performance, or it was used operationally, it earns a card back.

---

## Verified, do not re-litigate

- **Open-source scope.** The site claims three merged commits to PyTorch Geometric and
  one to einops, because that is what is verifiable. The GitHub profile also shows forks
  of `mlx`, `mlx-graphs` and `pytorch-frame` with no upstream commits; those are
  deliberately not claimed. A technical buyer checks this in under a minute. If there are
  contributions under another account or email, send them and the claim widens.
- **The Nov 2025 `content-update` copy is gone on purpose.** It described Genial Labs as
  having "a talented team of AI engineers and researchers" and listed twelve buzzwords
  under Expertise. Both work against the current positioning. Do not restore them from an
  older commit.

---

## Open items

- **Formspree delivery is still unproven.** Formspree requires the owner to confirm the
  first submission on a new form before it starts delivering. Submit the live form once,
  confirm the email, and this line can go. The `mailto:` fallback works regardless.
- **Plausible outbound-link tracking needs confirming.** The site is registered and
  `index.html` carries the per-site script Plausible issued
  (`/js/pa-r79QP5jHw7O4InoilgaQ0.js` plus the `plausible.init()` stub). That script has
  no `data-domain`; the domain is baked into the file. Optional features such as
  outbound-link tracking now live in the Plausible site settings rather than in the
  script filename, so switch outbound links on there or clicks on "Book a call" go
  uncounted. Then mark the booking link as a goal.
- **The blog has no RSS feed.** `https://project-delphi.github.io/ml-blog/index.xml`
  404s. Adding `feed: true` to the listing options in `_quarto.yml` in the `ml-blog` repo
  would enable one. The Writing section is now grouped by theme rather than by date, so
  it no longer looks stale between updates, but it is still hand-maintained.
- **The blog is on the wrong domain.** 80+ posts at `project-delphi.github.io` give all
  their topical authority to a domain that is not yours. Moving them to
  `genial-labs.com/writing` is the biggest inbound-search lever available, but it needs a
  static site generator and therefore a build step. Out of scope while the site is one
  hand-written page.
- **Favicon** is re-exported square at 96×96 from `assets/brain_logo.png`:
  `sips -z 96 96 ./assets/brain_logo.png --out ./assets/favicon.png` (lowercase `-z`
  takes height then width).
