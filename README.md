# brand-assets
My personal brand assets

<!-- COWORK-START -->

## What's Here

| File | Purpose |
|---|---|
| `tokens.css` | Canonical design tokens (CSS custom properties, v2.0.0). Import this into any project to inherit the full brand vocabulary. |
| `brand-guidelines.md` | Written brand reference: color, typography, spacing, elevation, motion, layout, component defaults, accessibility rules, and voice/tone notes. |
| `style-guide.html` | Live, browsable visual style guide. Open in a browser to see rendered swatches, type specimens, spacing scale, and component demos. Imports `tokens.css` directly. |
| `DK-Brand-v2.potx` | PowerPoint template with brand colors, EB Garamond headings, and Concourse T3 body text. Georgia serves as the theme-level heading fallback. Heading weight convention: titles and section/caption/header/row-label placeholders use EB Garamond Medium; the “Key Takeaways” point labels on the Three Key Points layout use EB Garamond SemiBold. Body and decorative non-heading runs use EB Garamond (Regular) where the body face is EB Garamond at all; the rest is Concourse T3. Color scheme is kept in sync with `DK Brand.xml`. |
| `DK-Brand-v2-systemfonts.potx` | Portable companion to `DK-Brand-v2.potx`, identical in layout, colors, and structure but with all custom typefaces replaced by web-safe system fonts. Headings use Georgia; body runs use Verdana (a Matthew Carter pairing matched to the same designer as Georgia, both engineered for screen). Every run that previously specified EB Garamond Medium or SemiBold now carries `b="1"` on Georgia. The notes-master theme’s Aptos/Aptos Display references are also replaced with Georgia and Verdana. No font embedding is required; the deck renders consistently on Windows, Mac, and PowerPoint for the web without substitution. Color scheme is kept in sync with `DK Brand.xml`. |
| `DK Brand.thmx` | Standalone Office theme (.thmx) for Word, Excel, and PowerPoint. Applies the DK Brand color scheme (navy + gold + extended palette, kept in sync with `DK Brand.xml`) and font scheme (Georgia headings, Concourse T3 body). Drop into the Office “Document Themes” folder to expose it in the Themes gallery. |
| `DK Brand.xml` | Standalone Office color scheme (.xml). Drop into the Office “Theme Colors” folder to expose the DK Brand palette in the “Customize Colors” menu without applying the full theme. The six theme accents map to navy (`accent1`), gold (`accent2`), mid-blue (`accent3`), terracotta (`accent4`), teal (`accent5`), and sage (`accent6`) — all sourced from `tokens.css`. Lighter tints for box backgrounds appear automatically under each accent in the PowerPoint color picker. |
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
