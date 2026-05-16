# brand-assets
My personal brand assets

<!-- COWORK-START -->

## What's Here

| File | Purpose |
|---|---|
| `tokens.css` | Canonical design tokens (CSS custom properties, v2.0.0). Import this into any project to inherit the full brand vocabulary. |
| `brand-guidelines.md` | Written brand reference: color, typography, spacing, elevation, motion, layout, component defaults, accessibility rules, and voice/tone notes. |
| `style-guide.html` | Live, browsable visual style guide. Open in a browser to see rendered swatches, type specimens, spacing scale, and component demos. Imports `tokens.css` directly. |
| `DK-Brand-v2.potx` | PowerPoint template with brand colors, EB Garamond headings, and Concourse T3 body text. Georgia serves as the theme-level heading fallback. |
| `palette-audit-2026-03-31.md` | WCAG 2.1 accessibility audit and remediation report from v2.0.0. |

## Quick Start

1. Copy `tokens.css` into your project (or link to it from this repo).
2. Load the web fonts:
   ```html
   <link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Libre+Franklin:wght@400;500;600;700&display=swap" rel="stylesheet">
   ```
3. Reference tokens as CSS custom properties (e.g., `color: var(--color-primary-800)`).
4. Consult `brand-guidelines.md` for usage rules and `style-guide.html` for visual reference.

## Brand at a Glance

**Primary:** Navy #002959 (Pantone 289 C)
**Accent:** Gold #FFD200 (Pantone 7405 C)
**Body typeface:** Libre Baskerville (serif)
**Heading typeface:** Libre Franklin (sans-serif)

<!-- COWORK-END -->
