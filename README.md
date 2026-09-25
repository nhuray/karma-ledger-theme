# karma-ledger-theme

The shared Tailwind CSS 4 theme for Karma: one `karma_ledger.css` (checked
against Tailwind 4.3) and the four Karma Ledger font files, consumed as a
pinned git tag by both the [karma-app.ca](https://github.com/nhuray/karma-app.ca)
marketing site and, later, the Karma Phoenix app. Never edited inside a
consumer — a theme change is always a new tag here, bumped in both projects.

## What's in here

- `assets/css/karma_ledger.css` — the `@font-face` rules, the Tailwind 4
  `@theme` tokens (colour, type, radii, shadows), base styles and the
  white-label accent hook.
- `priv/static/fonts/` — Geist, Geist Mono and Newsreader (roman + italic)
  variable fonts, each under the SIL Open Font License 1.1 (see the
  `*-OFL.txt` file beside it).

## Using it

Install a tag, never a branch:

```sh
npm install github:nhuray/karma-ledger-theme#v1.0.0
```

Import the stylesheet after Tailwind itself:

```css
/* src/styles/global.css */
@import "tailwindcss";
@import "@karma/ledger-theme/karma_ledger.css";
```

The stylesheet's `@font-face` rules point at `/fonts/<name>.woff2` — a
root-relative URL both projects share. Copy the font files into your own
public directory before build (Astro: `public/fonts/`, Phoenix:
`priv/static/fonts/`); see `karma-app.ca`'s `scripts/copy-theme-fonts.mjs`
for the Astro `prebuild` example.

## Versioning

Tag a new version (`v1.1.0`, …) for any change to the CSS or the fonts, then
bump the pinned tag in each consumer's `package.json` / `assets/package.json`
in the same change that needs it. Don't move an existing tag.
