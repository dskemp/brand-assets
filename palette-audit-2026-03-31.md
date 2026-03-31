# Brand Palette Audit — David S. Kemp

**Date:** 2026-03-31
**Scope:** Review `tokens.css` color palette for identity best practices and cross-medium suitability (web, documents, presentations, logo, print).
**Constraint:** Core brand colors (Primary 800 `#002959`, Primary 700 `#1E3A8A`, Accent 500 `#FFD200`) are fixed.

---

## Overall Assessment

The palette is well-structured, thoughtfully documented, and anchored to a strong navy-and-gold identity with clear institutional resonance. The token architecture — scale values, semantic aliases, legacy compatibility — is mature and shows real design-system discipline. That said, the audit identified several gaps that would surface in specific media contexts: print collateral, presentation slides, logo lockups, and accessible data visualization.

What follows are concrete, prioritized findings. Nothing here requires changing your core brand colors.

---

## 1. Accessibility Findings

### 1a. Confirmed Strengths

Your primary and neutral scales perform well against white backgrounds. Every combination used for body text and headings exceeds WCAG AAA (7:1), which is unusually strong:

| Pairing | Ratio | AA | AAA |
|---|---|---|---|
| Primary 800 on white | 14.37:1 | Pass | Pass |
| Primary 700 on white | 10.36:1 | Pass | Pass |
| Neutral 800 (body text) on white | 11.99:1 | Pass | Pass |
| Neutral 700 (secondary text) on white | 7.53:1 | Pass | Pass |
| Gold on navy (Primary 800) | 9.90:1 | Pass | Pass |
| Navy on gold | 9.90:1 | Pass | Pass |

### 1b. Issues Requiring Attention

**Neutral 500 (`#8B9096`) fails AA for normal text** at 3.22:1 against white. It passes only for large text (AA-large at 3.0:1). This token is aliased as `--color-text-faint`, which suggests it may be used for body-sized captions or placeholder text. If so, that usage would be non-compliant. *Recommendation:* Darken to approximately `#6B7280` (≈4.6:1) or restrict documented usage to large text and decorative elements only.

**Accent 500 (`#FFD200`) is unusable as a text color on light backgrounds.** At 1.45:1 against white, it fails every WCAG threshold. This is expected for a saturated yellow, but the palette currently provides no dark-gold token suitable for text. This becomes a real problem in presentations (gold text on white slides) and documents (gold headings). More on this in §3 below.

**Warning 700 (`#E65100`) fails AA on Warning 100 (`#FFF3E0`)** at 3.46:1. This means your semantic warning alerts, as specced, do not meet WCAG for normal-size text. *Recommendation:* Darken Warning 700 to approximately `#BF360C` (burnt sienna), which yields ≈5.4:1 on the same background.

**Warning 600 (`#F57C00`) fails AA on white** at 2.70:1. If used as standalone text or icon color, this is non-compliant. *Recommendation:* Same darkening approach, or restrict to background/border use.

---

## 2. Palette Completeness

### 2a. Accent Scale Is Top-Heavy

The accent (gold) scale runs from 600 to 50 — six light tints but only one darker value. Compare this to the primary scale, which has values from 900 down to 50. This asymmetry creates practical problems:

- **No accessible gold text color.** You need a dark gold (approximately 700–800 range) that reads as "gold" but carries enough contrast for body or heading text on white. Something in the `#7A6400`–`#5C4B00` range would fill this gap.
- **No "on-accent" token.** When gold is used as a background (buttons, badges, banners), there is no designated text color. The data shows that both Primary 800 and Neutral 900 work well on Gold 500 (9.90:1 and 11.24:1 respectively), but this should be codified as a token (e.g., `--color-on-accent`).

*Recommendation:* Add `--color-accent-700` (≈ `#8C7200`) and `--color-accent-800` (≈ `#5C4B00`). Add `--color-on-accent: var(--color-primary-800)` as a semantic alias.

### 2b. Missing "On-Primary" Token

Similarly, when Primary 800 or 700 serves as a background (nav bars, hero sections, footer), white text is the obvious choice, but there is no `--color-on-primary` token. Codifying this prevents implementers from guessing.

*Recommendation:* Add `--color-on-primary: var(--color-neutral-0)`.

### 2c. No Tertiary or Extended Palette

For data visualization, presentation charts, and multi-series graphics, navy and gold alone are insufficient. A brand identity guide typically includes 4–6 "extended" or "supporting" colors that harmonize with the core palette but provide enough variety for charts, category coding, and infographics. Without these, each project invents its own, and visual coherence erodes.

*Recommendation:* Define 3–4 supporting colors. Candidates that harmonize with navy/gold and maintain accessible contrast: a muted teal (e.g., `#2A7B88`), a warm slate (e.g., `#6B5B73`), and a desaturated coral or terracotta (e.g., `#C75C3A`). These should be documented as "extended palette — use for charts, diagrams, and multi-category interfaces" to keep the primary identity clean.

---

## 3. Cross-Medium Suitability

### 3a. Web — Strong

The token system is purpose-built for web and performs well. The fluid type scale, semantic aliases, and component tokens are all production-ready. The dark-mode stub is sensible. No issues beyond the contrast findings above.

### 3b. Presentations — Gaps

Slide decks typically need: (1) dark text on light backgrounds, (2) light text on dark backgrounds, and (3) accent text on both. Your palette handles cases 1 and 2 well. Case 3 is where the missing dark-gold values hurt — gold headings on white slides are a natural brand move but currently have no accessible token to support it.

Additionally, the lack of an extended palette means chart colors in presentations will be ad hoc.

### 3c. Print and Documents — Gaps

**CMYK mapping is absent.** For any printed collateral (business cards, letterhead, reports), your navy and gold need defined CMYK and Pantone equivalents. Digital hex values do not translate reliably to print without explicit mapping. Primary 800 (`#002959`) maps roughly to Pantone 289 C; Accent 500 (`#FFD200`) maps roughly to Pantone 7405 C. These should be documented in the tokens file or in a companion brand guide.

**PDF export and Word/PowerPoint themes** often reference RGB rather than hex. Adding explicit RGB triplet tokens (or at minimum a comment block with RGB equivalents) reduces conversion errors.

### 3d. Logo — Workable but Verify

Navy on white, gold on navy, and white on navy all have strong contrast ratios. The palette supports standard logo lockup variations. The one risk is a gold-on-white logo variant — there is no accessible version of gold for that context. A dark-gold (`accent-700` or `accent-800`) would serve as the logo color in white-background contexts where the full-saturation gold washes out.

---

## 4. Perceptual Uniformity

### 4a. Primary Scale

The luminance steps in the primary scale are reasonably even through the mid-range (600–300) but compress at the extremes. The jump from 900 to 800 (ΔLum = 0.013) is perceptually small — these two values are nearly indistinguishable in many display conditions. Conversely, the 100-to-50 jump (ΔLum = 0.10) is much larger than the 200-to-100 jump (ΔLum = 0.22) would predict. This is not a serious problem, but be aware that the 900 value may not read as distinct from 800 in UI contexts.

### 4b. Accent Scale

The jump from 600 to 500 (ΔLum = 0.28) is dramatically larger than any other step in the scale. This means there is a perceptual "cliff" between your darkest gold and your brand gold — no intermediate value bridges the gap. Adding a 700 value (as recommended above) would also smooth this transition.

---

## 5. Summary of Recommendations

| Priority | Recommendation | Rationale |
|---|---|---|
| **High** | Add `--color-accent-700` (~`#8C7200`) and `--color-accent-800` (~`#5C4B00`) | Enables accessible gold text on light backgrounds |
| **High** | Add `--color-on-primary` and `--color-on-accent` semantic tokens | Prevents guesswork; required for any component system |
| **High** | Darken Warning 700 to ~`#BF360C` | Current value fails WCAG on its own background |
| **Medium** | Darken Neutral 500 to ~`#6B7280` or restrict usage to large text | Current value fails AA at body text size |
| **Medium** | Define 3–4 extended/supporting colors for data visualization | Prevents ad hoc color choices in charts and diagrams |
| **Medium** | Document CMYK/Pantone equivalents for primary and accent | Required for any print application |
| **Low** | Consider adding `--color-accent-900` to complete the dark end | Improves perceptual uniformity of the accent scale |
| **Low** | Add RGB triplet comments for key brand colors | Reduces conversion errors in non-web contexts |

---

*This audit was conducted programmatically using WCAG 2.1 relative-luminance calculations. All contrast ratios are verifiable against the W3C contrast formula. No subjective color judgments were made without supporting data.*
