# Malika Rasulova — personal site

Single-file static site in three languages (EN / UZ / RU). No build step.

- `index.html` — the site itself (this is the file GitHub Pages serves)
- `page.html` — the Claude artifact version (same content, without `<head>`); not published
- `portrait.jpg` — square portrait used as the round avatar

## Editing

Look for `<!-- EDIT -->` comments in `index.html`. What to change:

1. Contacts: email, Telegram, LinkedIn, GitHub (in the rail and the Contact section)
2. Monogram/name in the `.monogram` and `h1` elements
3. Texts: the `I18N` object in the `<script>` block at the bottom holds all three
   languages (`en`, `uz`, `ru`). The English strings also appear in the HTML above,
   so if you change `en`, update the matching `data-i18n` element too.
4. Project descriptions — keys `p1`…`p8`

The language switcher is top-left; the choice is remembered in `localStorage`.

## Publishing to GitHub Pages

### Option A — profile site at `malikarasulova.github.io`

1. On GitHub, create a new **public** repo named exactly `MalikaRasulova.github.io`
   (do not add a README — keep it empty).
2. In this folder, run:

```sh
git remote add origin https://github.com/MalikaRasulova/MalikaRasulova.github.io.git
git push -u origin main
```

3. Open **Settings → Pages**. Source: `Deploy from a branch`,
   Branch: `main` / `(root)` → **Save**.
4. After 1–2 minutes the site is live at **https://malikarasulova.github.io**

### Option B — inside an existing repo

Copy `index.html` into the root of that repo, push, then
**Settings → Pages → Deploy from a branch → `main` / `(root)` → Save**.

URL: `https://malikarasulova.github.io/<repo-name>/`

## About the 404

`There isn't a GitHub Pages site here` means one of three things:

- the repo has not been pushed yet,
- Pages is not enabled in **Settings → Pages**, or
- there is no `index.html` in the folder Pages is serving from.

The git repo in this folder already has the first commit; only `git remote add`
and `git push` are left.
