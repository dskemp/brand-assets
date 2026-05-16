# Changelog

## 2026-05-15

### Substantive
- **Brand package created.** Drafted comprehensive brand guidelines (`brand-guidelines.md`) covering color palette (with provenance, accessibility notes, and print equivalents), typography (typeface pairing, fluid type scale, heading conventions, measure), spacing (8px grid with semantic aliases), elevation, borders/radii, motion, layout containers, z-index scale, component defaults (nav, cards, buttons, inputs), accessibility requirements, and brief voice/tone guidance.
- **Live style guide built** (`style-guide.html`). Self-contained HTML page importing `tokens.css` that renders all brand elements visually: color swatches for primary, accent, neutral, semantic, and extended palettes; on-surface contrast pairings; type specimens and full scale; spacing bars; shadow/elevation cards; border radius demos; and interactive component examples (nav, buttons, card, form inputs, alerts). Includes print equivalents table.

- **Presentation typography formalized.** Updated `DK-Brand-v2.potx` to use EB Garamond (bold, 38pt) for slide headings across all 13 layouts that contain heading text. Georgia retained as theme-level fallback for machines without EB Garamond installed. Concourse T3 remains the body font. Added "Presentation Typefaces" section (§2.5) to `brand-guidelines.md` documenting the pairing, rationale for web/presentation divergence, fallback behavior, and cross-context summary.

### Technical
- Updated `README.md` with file inventory, quick-start instructions, and brand-at-a-glance summary (within COWORK markers).
- Backed up original template as `DK-Brand-v2.potx.bak` before modifying.

## 2026-03-31

### Substantive
- **Palette audit and remediation (tokens.css v2.0.0).** Conducted programmatic WCAG 2.1 contrast audit of entire palette; corrected all failing pairs.
  - **Accent scale extended:** Added `accent-900` (#3D3200), `accent-800` (#5C4B00), `accent-700` (#806800) — dark gold values that allow gold to serve as accessible text on light backgrounds (presentations, documents, logo lockups).
  - **On-surface tokens added:** `--color-on-primary` (white) and `--color-on-accent` (navy) codify text colors for navy and gold backgrounds. `--color-accent-text` provides accessible gold for use as a text color.
  - **Warning 700 darkened** from #E65100 to #BF360C — old value failed AA (3.46:1) on its own warning-100 background; new value passes (5.11:1). Warning 600 shifted accordingly.
  - **Neutral 500 darkened** from #8B9096 to #697077 — old value failed AA (3.22:1) on white; new value passes (5.02:1).
  - **Extended palette defined:** Four supporting colors for data visualization and multi-category interfaces: teal (#2A7B88), slate (#6B5B73), terracotta (#AD4E2D), sage (#4A7C59). All pass AA on white.
  - **Institutional provenance documented:** Added origin comments tracing primary/accent palette to St. Mark's School of Texas (PMS 540 C navy, Gold #FFD200), Rice University (#00205B), UC Berkeley (#002676, California Gold #FDB515), Justia Inc. (#06357A), and Ropes & Gray LLP (RG Dark Blue #01426A, RG Blue #006699, RG Gray #727D84). Confirmed brand gold (#FFD200) is an exact match to St. Mark's Gold per smtexas.org. Ropes & Gray palette sourced from official brand guide.
  - **Print equivalents added:** Pantone and CMYK mappings for primary 800, primary 700, accent 500, and accent 700 documented in header block.

### Technical
- Bumped tokens.css version from 1.0.0 to 2.0.0 (breaking: neutral-500 and warning-700 values changed).
- Created `palette-audit-2026-03-31.md` — full audit report with contrast ratios, perceptual uniformity analysis, and recommendations.
