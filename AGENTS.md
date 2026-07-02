# Golova Design System

- This repo is the Golova design-system reference, not an application and not an npm package.
- The deliverable is a static documentation/demo page that records design rules, tokens, components, and brand assets.
- There is no `package.json`, lockfile, CI config, or repo-defined build/test/lint command.
- Primary entrypoint is `index.html`; it imports `css/tokens.css` before `css/components.css`. Keep that order.
- Verify changes by opening or serving `index.html` and checking desktop plus the existing mobile breakpoint at `max-width:960px`.

# Design System Rules

- `css/tokens.css` owns primitive, semantic, spacing, radius, shadow, motion, and font tokens; `css/components.css` should be built on those tokens rather than duplicating values.
- Treat the page as a source of design-system rules, not just a visual mockup; keep examples aligned with the token/component contract.
- Color model is intentionally three-tiered: primitive -> semantic -> component. Components should use semantic tokens where possible, not primitive colors directly.
- The neutral scale is intentionally uneven (`90, 80, 70, 50, 30, 20, 0`); do not normalize or renumber it.
- There is no official warning token yet. Rating stars use `--_placeholder-warning:#F5A623`; add a real palette token before broadening warning usage.
- Forms are deliberately angular: all form controls use `--radius-form` (`4px`). The switch track is the only pill-shaped form control.

# Assets And Fonts

- Brand assets live in `logos/`: `logo_2.svg` mark, `logo_1.svg` corporate lockup, `logo_market.svg` product lockup.
- On dark backgrounds, existing SVG lockups are inverted with `.on-dark img { filter:invert(1) brightness(2); }`.
- Roboto Flex is loaded from Google Fonts for all UI text.
- `fonts/PragmataProMono-Regular.woff2` is licensed for limited web use and is reserved for logo/decorative/display accents; do not use it for body copy.
- Icons in examples come from the Bootstrap Icons CDN class pattern (`bi bi-*`) in `index.html`.
