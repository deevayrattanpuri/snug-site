# snug-site

The website for **Snug**, an Android photo resizing app — marketing pages, the
blog, and the Privacy Policy and Terms of Service that the Play Store listing
links to.

Plain static HTML and one stylesheet. No build step, no framework, no
dependencies. GitHub Pages serves `main` directly.

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Home — hero, what it does, how it works, tools, privacy, presets, screenshots, free forever, FAQ, latest posts, legal |
| `what-it-does.html` | Every tool explained in depth, with a specifications table and FAQ |
| `blog/index.html` | Blog, page 1 — nine post tiles in a 3×3 grid |
| `blog/page-2.html`, `blog/page-3.html` | Blog pages 2 and 3 |
| `blog/<slug>.html` | One file per article (27 of them) |
| `privacy.html` | Privacy Policy |
| `terms.html` | Terms of Service |
| `style.css` | The whole design system — tokens, components, light and dark |
| `sitemap.xml`, `robots.txt` | For search engines |

## Design

Colours are sampled from the app's own store assets. `#00897B` is the primary —
the same teal used for filled buttons and cards in the app — and the brand
gradient runs `#2FC09A → #008375`. Everything is defined as CSS custom
properties at the top of `style.css`, with a mirrored block for dark mode, so
re-theming means editing those two blocks and nothing else.

There are **no external fonts or network requests**. The site is entirely
self-contained, which keeps it fast and is consistent with what the Privacy
Policy promises.

## Assets

`assets/` holds the Play Store artwork plus web-optimised versions:

- `icon*.png` — app icon, used as the favicon and the wordmark
- `feature-graphic.webp` — store feature graphic, also the social preview image
- `screen-*.webp` — the three store screenshots, with `@540` versions for `srcset`
- `phone-*.webp` — the phone mockups cut out of those screenshots with
  transparent rounded corners, for placing on any background

## Adding a blog post

1. Copy any file in `blog/` as a starting point and edit the content, the
   `<title>`, the description, the canonical link and the JSON-LD block.
2. Add a tile for it at the top of `blog/index.html`, inside `<ul class="posts">`.
3. Move the last tile on page 1 to the top of `blog/page-2.html`, and so on, so
   each page keeps nine tiles.
4. Add the new URL to `sitemap.xml`.

Categories map to a cover colour class in `style.css` — `c-sizing`,
`c-formats`, `c-privacy`, `c-presets`, `c-workflow`, `c-storage`.

## Editing the legal pages

Change the "Last updated" date at the top whenever the wording changes, and
keep the two files consistent with each other. Both are linked from the Play
Store listing, so they should be published before any change they describe
takes effect.

## Previewing locally

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
```
