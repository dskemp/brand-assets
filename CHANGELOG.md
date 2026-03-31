# Changelog

## 2026-03-31

### Substantive
- **Palette audit and remediation (tokens.css v2.0.0).** Conducted programmatic WCAG 2.1 contrast audit of entire palette; corrected all failing pairs.
  - **Accent scale extended:** Added `accent-900` (#3D3200), `accent-800` (#5C4B00), `accent-700` (#806800) — dark gold values that allow gold to serve as accessible text on light backgrounds (presentations, documents, logo lockups).
  - **On-surface tokens added:** `--color-on-primary` (white) and `--color-on-accent` (navy) codify text colors for navy and gold backgrounds. `--color-accent-text` provides accessible gold for use as a text color.
  - **Warning 700 darkened** from #E65100 to #BF360C — old value failed AA (3.46:1) on its own warning-100 background; new value passes (5.11:1). Warning 600 shifted accordingly.
  - **Neutral 500 darkened** from #8B9096 to #697077 — old value failed AA (3.22:1) on white; new value passes (5.02:1).
  - **Extended palette defined:** Four supporting colors for data visualization and multi-category interfaces: teal (#2A7B88), slate (#6B5B73), terracotta (#AD4E2D), sage (#4A7C59). All pass AA on white.
  - **Institutional provenance documented:** Added origin comments tracing primary/accent palette to St. Mark's School of Texas (PMS 540 C, athletic gold), Rice University (#00205B), UC Berkeley (#002676, California Gold #FDB515), Justia Inc. (#06357A), and Ropes & Gray LLP.
  - **Print equivalents added:** Pantone and CMYK mappings for primary 800, primary 700, accent 500, and accent 700 documented in header block.

### Technical
- Bumped tokens.css version from 1.0.0 to 2.0.0 (breaking: neutral-500 and warning-700 values changed).
- Created `palette-audit-2026-03-31.md` — full audit report with contrast ratios, perceptual uniformity analysis, and recommendations.
