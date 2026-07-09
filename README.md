# Golova Design System

Static reference page for the Golova design system: tokens, components, typography, logos, and usage guidance for the product ecosystem.

Repository: <https://github.com/ulyru/design-system>

Live version: <https://golova-ds.rubashkin.xyz>

## Open Locally

- Open `index.html` directly in a browser, or serve the folder with any static server.
- Example: `python3 -m http.server` from this directory, then open `http://localhost:8000`.
- There is no package install, build, lint, or test step in this repo.

## Structure

- `index.html` is the reference/demo page and imports styles in this order: `css/tokens.css`, then `css/components.css`.
- `css/tokens.css` defines primitive, semantic, spacing, radius, shadow, motion, and font tokens.
- SaaS platform color tokens are exposed as `content-*`, `background-*`, `border-*`, and `category-*` CSS variables alongside legacy-compatible `neutral/*` and `brand/*` variables.
- `css/components.css` defines reusable component classes built on top of tokens.
- `tokens.json` is the machine-readable token contract for agents, scripts, Figma workflows, and future exports.
- `AI_USAGE.md` is the quick instruction file for Claude Code, Codex, and other AI agents building Golova prototypes.
- `logos/` contains the Golova mark and lockups.
- `fonts/` contains the licensed PragmataPro Mono web font used only for logo/decorative/display accents.
- `DESIGN_SYSTEM_GUIDE.md` is a Russian-language working memo for maintaining the system with a designer-led workflow.

## Design Rules

- Keep the color system three-tiered: primitive -> semantic -> component.
- Prefer semantic tokens in components instead of hard-coded primitive colors.
- Do not normalize the neutral scale; its uneven steps are intentional: `90, 80, 70, 50, 30, 20, 0`.
- Use SaaS platform tokens for product handoff naming: `content-neutral-*`, `content-informative`, `background-primary`, `border-informative`, `category-equipment`, `warning-rating`, etc.
- Forms are intentionally angular and use `--radius-form` (`4px`); the switch track is the only pill-shaped form control.
- Rating stars use the official `warning/rating` token: `--warning-rating:#F5A623`.
- UI typography is routed through `--font-body`; the active family can switch via `data-ui-font="roboto|inter|pragmata"`.

## Verification

After changes, check `index.html` in a browser on desktop and at the existing mobile breakpoint (`max-width:960px`).
