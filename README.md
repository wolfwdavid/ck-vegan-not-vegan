# Vegan Not Vegan — flipbook edition

A mobile-first reading app for the *Vegan Not Vegan* guide book by Cosmic Kitty in Space. One screen per page of the book, swipe or arrow-key between them, jump to any section from the contents menu, and fill in the "Your Last…" worksheet (answers stay on your device).

Live: https://wolfwdavid.github.io/ck-vegan-not-vegan/

## How it works

- `data/content.json` — every screen of the book, transcribed from the source PDF (93 screens: cover, essays, recipes, A-Z pantry, B12, resources, worksheet, bio).
- `js/templates.js` — one render function per screen type.
- `js/app.js` — the flipbook engine: swipe/keyboard/edge-tap navigation, progress bar, contents menu, URL-hash deep links (`#recipe-milk-23`, `#pantry-m`), worksheet persistence.
- `css/style.css` — cream paper, Oswald headlines, Source Serif body.
- `ck.json` — manifest read by the CK dashboard (https://wolfwdavid.github.io/ck/).

No build step: GitHub Pages serves the `master` branch as-is.

## Regenerating content from the PDF

```
uv run --with pymupdf python scripts/extract_assets.py   # images + link annotations
uv run python scripts/merge_content.py                   # data/batch*.json -> data/content.json
```
