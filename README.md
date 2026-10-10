# Malika Rasulova — personal site

Single-file static site in three languages (EN / UZ / RU). No build step.
Live at **https://malikarasulova.github.io**

- `index.html` — the whole site: markup, design tokens, styles and the three dictionaries
- `portrait.jpg` — the hero portrait (cropped to 3:4 and masked into an arch, so a square source works)

## Design

A warm editorial portfolio. One giant cropped word of display type across the
top, the portrait sitting on a terracotta disc with a rotating caption ring, a
scrolling stack strip, and the record as numbered rounded cards — the current
job inverted to the dark block so it reads first.

Four faces, four jobs:

| Role | Face | Where |
| --- | --- | --- |
| The cropped word, figures | Oswald 700 | `BACKEND`, the stat numbers, the job years |
| Names and headings | Prata | the name, every `h2`, company names, the contact call |
| Reading | Golos Text | body text, list items, skill values |
| Small labels | IBM Plex Mono | eyebrows, dates, chips, the top strip, the footer |

All four carry Cyrillic, so the Russian version uses the same typography as the
other two.

Colour lives in `:root` as tokens: cream paper, warm near-black, one terracotta
doing every signal, and an amber used only for what is live right now (the
"open to offers" dot and the Now block). `--dark` is the inverted block used by
the sticky nav, the Now strip, the current job, the AI note and the contact card.

Themes: the bare `:root` block holds the light values; the dark values are
repeated in `@media (prefers-color-scheme: dark)` (guarded so an explicit light
choice wins) and in `:root[data-theme="dark"]` (so the toggle wins too). Change a
colour in all three places or the two themes drift apart.

Motion: the marquee and the caption ring loop, the "live" dots breathe, the hero
rises on load, and sections fade in as they come into view. The reveal is armed
by JS (`data-reveal` on `<html>`), so with JS off everything stays visible.
`prefers-reduced-motion` switches all of it off.

## Editing

Look for `<!-- EDIT -->` comments in `index.html`. What to change:

1. **Contacts** — email, Telegram, LinkedIn, GitHub, all inside `.contact-card`.
   The email is the big pill (`.mail-btn`); the rest are tiles. The GitHub link
   also appears as the second hero button.
2. **Name** — the `h1` (two `span`s; `.l2` is the terracotta half) and the
   `.monogram` in the nav.
3. **Texts** — the `I18N` object in the `<script>` block at the bottom holds all
   three languages (`en`, `uz`, `ru`). Keys match the `data-i18n` attributes in
   the markup. The English strings also sit in the HTML above (that is what shows
   before JS runs), so when you change `en`, change the matching element too.
4. **Jobs** — one `<article class="job">` each, with its own `01`…`05` badge and a
   big year. The body is a `data-i18n` container whose dictionary string carries
   its own `<h4>` and `<ul>`, so edit those inside the `I18N` object, not in the
   markup. `class="current"` inverts a card to the dark block — move it when the
   job changes. The stack chips are plain `<span class="chip">` in the markup.
5. **Figures** — the four `.stat` tiles. The numbers are hard-coded in the markup
   (they are language-neutral); their labels are the `st_*` keys.
   Today: 4 years, 5 companies, 8 named systems, 3 languages. Keep them true.
6. **Projects** — keys `p1`…`p8`, one `<a class="project">` per repo.
7. **Metadata** — `og:*` tags and the JSON-LD `Person` block at the end of the
   file also carry the name, role and links. Update them when the contacts change.

The language switcher and the AUTO / LIGHT / DARK toggle sit in the nav pill;
both remember the choice in `localStorage`.

## Checking a change locally

```sh
python -m http.server 8765
```

Then open `http://localhost:8765`. Opening `index.html` straight from the
filesystem works too, but a server matches what GitHub Pages does.

## Publishing

Pages is already serving `main` / `(root)`, so a push is the whole deploy:

```sh
git add -A && git commit -m "..." && git push
```

The live site updates a minute or two later.
