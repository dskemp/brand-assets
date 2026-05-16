# Brand Guidelines — David S. Kemp

**Version:** 1.0.0
**Date:** 2026-05-15
**Token source:** `tokens.css` v2.0.0

These guidelines govern the visual identity of the David S. Kemp personal brand across digital and print media. They draw from a design token system rooted in institutional affiliations spanning St. Mark's School of Texas, Rice University, UC Berkeley, Justia Inc., and Ropes & Gray LLP. The result is a palette that feels both scholarly and distinctive — deep navy blues paired with a warm institutional gold.

All CSS custom properties referenced below are defined in `tokens.css`, the canonical source of truth.

---

## 1. Color

### 1.1 Core Palette

The brand rests on two colors: a navy blue and a gold. Every other color in the system plays a supporting role.

#### Primary — Navy Blue

| Token | Hex | Role |
|---|---|---|
| `--color-primary-900` | `#001A3A` | Deepest navy; use for high-contrast backgrounds |
| `--color-primary-800` | `#002959` | **Brand primary.** Default navy for backgrounds, headers, and key UI surfaces |
| `--color-primary-700` | `#1E3A8A` | Mid-blue; hover states, secondary navy elements |
| `--color-primary-600` | `#2B4FA3` | Interactive mid-tone |
| `--color-primary-500` | `#3B63B8` | Lighter interactive blue |
| `--color-primary-400` | `#5A80CC` | Links in dark contexts |
| `--color-primary-300` | `#8BA5DB` | Decorative, light fills |
| `--color-primary-200` | `#B8CAE8` | Subtle tints |
| `--color-primary-100` | `#E0E8F5` | Very light wash |
| `--color-primary-50`  | `#F0F4FA` | Near-white background tint |

**Provenance:** Primary 800 sits nearest Rice Blue (#00205B). Primary 700 aligns with Justia Blue (#06357A). The range between them captures St. Mark's PMS 540 C (≈ #003B6F) and Ropes & Gray's dark navy wordmark (#01426A).

#### Accent — Gold

| Token | Hex | Role |
|---|---|---|
| `--color-accent-900` | `#3D3200` | Deepest gold; rarely used |
| `--color-accent-800` | `#5C4B00` | Very dark gold |
| `--color-accent-700` | `#806800` | **Accessible gold text** (4.98:1 on white). Use when gold must appear as text on light backgrounds |
| `--color-accent-600` | `#C9A600` | Dark gold fill |
| `--color-accent-500` | `#FFD200` | **Brand gold.** Fills, highlights, accent bars, and decorative elements |
| `--color-accent-400` | `#FFE04D` | Light gold |
| `--color-accent-300` | `#FFEB80` | Softer gold fill |
| `--color-accent-200` | `#FFF3B3` | Tint |
| `--color-accent-100` | `#FFF9DB` | Very light gold wash |
| `--color-accent-50`  | `#FFFCED` | Near-white gold tint |

**Provenance:** Accent 500 is St. Mark's Gold (#FFD200), reinforced by UC Berkeley's California Gold (#FDB515).

**Critical accessibility note:** Accent 500 (#FFD200) has a contrast ratio of only 1.45:1 against white. Never use it as text on light backgrounds. When gold text is needed, use Accent 700 (#806800) or darker.

#### Neutrals

| Token | Hex | Role |
|---|---|---|
| `--color-neutral-900` | `#1A202C` | Near-black |
| `--color-neutral-800` | `#2D3748` | **Text primary** |
| `--color-neutral-700` | `#4A5568` | Text secondary, dark gray |
| `--color-neutral-600` | `#718096` | Subtle text |
| `--color-neutral-500` | `#697077` | Secondary gray (5.02:1 on white, AA compliant) |
| `--color-neutral-400` | `#A0AEC0` | Disabled states, placeholder text |
| `--color-neutral-300` | `#CBD5E0` | Strong borders |
| `--color-neutral-200` | `#E2E8F0` | Default borders |
| `--color-neutral-100` | `#EDF2F7` | Light borders, subtle fills |
| `--color-neutral-50`  | `#F5F6F7` | Light gray background |
| `--color-neutral-0`   | `#FFFFFF` | White |

**Provenance:** Neutral 600–700 aligns with Ropes & Gray's RG Gray (#727D84) and RG Dark Gray (#545F66).

### 1.2 On-Surface Tokens

When using brand colors as backgrounds, pair them with the designated on-surface text color:

| Background | Text Token | Text Color | Contrast Ratio |
|---|---|---|---|
| Navy (`--color-primary-800`) | `--color-on-primary` | White | Excellent (15.39:1) |
| Gold (`--color-accent-500`) | `--color-on-accent` | Navy (#002959) | Exceptional (9.90:1) |

These pairings are non-negotiable. Navy backgrounds always receive white text. Gold backgrounds always receive navy text.

### 1.3 Semantic Colors

For status indicators, alerts, and feedback:

| Purpose | Foreground (700) | Background (100) | Border |
|---|---|---|---|
| Success | `#1B5E20` | `#E8F5E9` | `#A5D6A7` |
| Error | `#B71C1C` | `#FFEBEE` | `#EF9A9A` |
| Warning | `#BF360C` | `#FFF3E0` | `#FFCC80` |
| Info | `#1565C0` | `#E3F2FD` | `#90CAF9` |

### 1.4 Extended Palette

For data visualization, charts, and multi-category interfaces. All pass WCAG AA (≥ 4.5:1) on white.

| Name | Hex | Contrast on White |
|---|---|---|
| Teal | `#2A7B88` | 4.90:1 |
| Slate | `#6B5B73` | 6.23:1 |
| Terracotta | `#AD4E2D` | 5.38:1 |
| Sage | `#4A7C59` | 4.86:1 |

When four data series are needed, use them in this order: teal, slate, terracotta, sage. For fewer series, select based on semantic fit.

### 1.5 Print Equivalents

For printed collateral, business cards, and physical signage:

| Color | Hex | Pantone | CMYK |
|---|---|---|---|
| Brand Navy | `#002959` | 289 C | 100 / 78 / 30 / 25 |
| Mid-Blue | `#1E3A8A` | 2758 C | 88 / 70 / 0 / 0 |
| Brand Gold | `#FFD200` | 7405 C | 0 / 16 / 100 / 0 |
| Dark Gold | `#806800` | 133 C | 18 / 28 / 100 / 10 |

---

## 2. Typography

The brand uses different typeface pairings for web and presentation contexts. The rationale: slides and web pages impose different demands on type. Slides are projected, viewed at a distance, and dominated by headings; web pages are read at arm's length, with body text carrying the load. The pairings are chosen to serve each context well while sharing a common aesthetic register — scholarly, precise, warm.

### 2.1 Web Typefaces

**Libre Baskerville** (serif) serves as the web body typeface. Its generous x-height and sturdy serifs provide excellent screen readability while preserving the gravitas appropriate to legal and academic contexts.

**Libre Franklin** (sans-serif) serves web headings, navigation, UI labels, and any context where a cleaner, more compact voice is needed. It also functions as the UI typeface for buttons, form labels, and interactive elements.

**Monospace** falls back through SF Mono, Cascadia Code, and Fira Code. Use for code samples, data tables with fixed-width requirements, or technical content.

#### Loading Web Fonts

Any project consuming `tokens.css` must load the typefaces:

```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Libre+Franklin:wght@400;500;600;700&display=swap" rel="stylesheet">
```

### 2.2 Type Scale

The scale uses CSS `clamp()` for fluid responsive sizing. The ratio is approximately 1.2 (minor third), anchored at 1rem = 16px.

| Token | Range | Typical Use |
|---|---|---|
| `--text-xs` | 13–14px | Fine print, captions |
| `--text-sm` | 14–16px | Metadata, small UI labels |
| `--text-base` | 17–18px | Body text |
| `--text-lg` | 18–20px | Lead paragraphs, large body |
| `--text-xl` | 20–24px | h4, card titles |
| `--text-2xl` | 22–30px | h3, section subheads |
| `--text-3xl` | 26–38px | h2, section titles |
| `--text-4xl` | 30–46px | h1, page titles |
| `--text-5xl` | 35–60px | Display / hero (use sparingly) |

### 2.3 Heading Conventions

Headings use Libre Franklin, semibold or bold weight, with tight leading and slight negative letter spacing. Body text uses Libre Baskerville at regular weight with normal to relaxed leading.

| Element | Font | Weight | Size Token | Line Height | Letter Spacing |
|---|---|---|---|---|---|
| h1 | Libre Franklin | 700 | `--text-4xl` | `--leading-tight` (1.25) | `--tracking-tight` |
| h2 | Libre Franklin | 700 | `--text-3xl` | `--leading-tight` (1.25) | `--tracking-tight` |
| h3 | Libre Franklin | 600 | `--text-2xl` | `--leading-snug` (1.35) | `--tracking-normal` |
| h4 | Libre Franklin | 600 | `--text-xl` | `--leading-snug` (1.35) | `--tracking-normal` |
| Body | Libre Baskerville | 400 | `--text-base` | `--leading-relaxed` (1.65) | `--tracking-normal` |
| Caption | Libre Franklin | 400 | `--text-xs` | `--leading-normal` (1.5) | `--tracking-wide` |

### 2.4 Measure (Line Length)

Optimal line length for sustained reading is 65 characters (`--measure`). Narrow columns (sidebars, pull quotes) should use `--measure-narrow` (45ch). Wide layouts (dashboards, tables) may extend to `--measure-wide` (85ch), but body text should never exceed it.

### 2.5 Presentation Typefaces

Presentations use a different pairing optimized for projected display at large sizes.

**EB Garamond** (serif) serves as the heading typeface in slide decks. It is an old-style serif with high stroke contrast that looks refined and elegant at 36pt+ — qualities that reward the large rendering sizes typical of slide headings. EB Garamond also carries an institutional connection to Ropes & Gray LLP. It is freely available from Google Fonts (OFL license; embedding unrestricted).

**Concourse T3** (sans-serif) serves as the body typeface in slide decks. Designed by Matthew Butterick, the T3 weight is calibrated for running text rather than display. It is a commercial font from MB Type; confirm that the license permits .pptx embedding before distributing decks with embedded fonts.

#### Presentation Typography Summary

| Element | Font | Size | Weight |
|---|---|---|---|
| Slide title | EB Garamond | 38pt | Bold |
| Body text (level 1) | Concourse T3 | 20pt | Regular |
| Body text (level 2) | Concourse T3 | 16pt | Regular |

#### Fallback Behavior

The PowerPoint template (`DK-Brand-v2.potx`) sets Georgia as the theme-level heading font. If EB Garamond is not installed on the presenting machine, PowerPoint falls back to Georgia — a reasonable substitution, as both are traditional serifs. Concourse T3 falls back to the system default sans-serif (typically Calibri), which is less ideal; always embed fonts or export to PDF before sharing externally.

#### Cross-Context Summary

| Context | Heading | Body | Notes |
|---|---|---|---|
| Web | Libre Franklin (sans) | Libre Baskerville (serif) | Loaded from Google Fonts via `tokens.css` |
| Presentations | EB Garamond (serif) | Concourse T3 (sans) | Template: `DK-Brand-v2.potx`; embed fonts or export to PDF for portability |

---

## 3. Spacing

The spacing system follows an 8px base grid. Use the semantic aliases for most contexts:

| Alias | Step | Value | Use |
|---|---|---|---|
| `--space-xs` | 2 | 8px | Tight gaps between related elements |
| `--space-sm` | 4 | 16px | Padding inside compact components |
| `--space-md` | 6 | 24px | Default content padding |
| `--space-lg` | 8 | 32px | Section padding, card interiors |
| `--space-xl` | 12 | 48px | Major section breaks |
| `--space-2xl` | 16 | 64px | Page-level vertical rhythm |
| `--space-3xl` | 24 | 96px | Hero sections, dramatic white space |

When in doubt, use more space rather than less. The brand aesthetic leans toward generous white space — it signals confidence and clarity.

---

## 4. Elevation

Shadows create hierarchy. The system provides four levels plus semantic aliases:

| Level | Alias | Use |
|---|---|---|
| 0 | — | Flat elements, inline content |
| 1 | `--shadow-sm` | Cards at rest, subtle lift |
| 2 | `--shadow-md` | Cards on hover, dropdown menus |
| 3 | `--shadow-lg` | Popovers, floating panels |
| 4 | `--shadow-xl` | Modals, dialogs |

A gold accent shadow (`--shadow-accent`) is available for gold-highlighted elements. Use it sparingly — on featured cards, callouts, or primary CTAs with gold accents.

---

## 5. Borders and Radii

Default border radius is 6px (`--radius-md`), which gives components a slightly softened edge without appearing rounded or playful. Cards use 8px (`--radius-lg`). Pill shapes (tags, badges) use `--radius-full`.

Borders default to 1px solid in `--color-border` (#E2E8F0). Use `--border-medium` (2px) for emphasis or active states.

---

## 6. Motion

Transitions should feel responsive but not abrupt:

| Token | Duration | Use |
|---|---|---|
| `--duration-fast` | 100ms | Hover color changes, focus rings |
| `--duration-normal` | 200ms | Most transitions (opacity, transform) |
| `--duration-slow` | 350ms | Expanding panels, slide-ins |
| `--duration-slower` | 500ms | Page-level transitions, complex animations |

The default easing curve (`--ease-default`) is `cubic-bezier(0.4, 0, 0.2, 1)`, a slightly decelerated curve that feels natural. Use `--ease-spring` for playful micro-interactions (toggle switches, success checkmarks).

---

## 7. Layout

### Container Widths

| Token | Width | Use |
|---|---|---|
| `--width-prose` | 65ch | Long-form reading |
| `--width-narrow` | 640px | Single-column forms, narrow content |
| `--width-content` | 820px | Articles, blog posts |
| `--width-container` | 1100px | Standard page container |
| `--width-wide` | 1280px | Dashboard layouts, wide content |

### Z-Index Scale

Rather than ad-hoc z-index values, consume these tokens:

| Token | Value | Use |
|---|---|---|
| `--z-base` | 0 | Default stacking |
| `--z-raised` | 10 | Slightly elevated elements |
| `--z-dropdown` | 100 | Dropdowns, select menus |
| `--z-sticky` | 200 | Sticky headers, sidebars |
| `--z-overlay` | 300 | Overlays, backdrops |
| `--z-modal` | 400 | Modals, dialogs |
| `--z-toast` | 500 | Toast notifications |

---

## 8. Component Defaults

These tokens provide opinionated starting points. Override them per-project as needed.

**Navigation:** 64px height, near-opaque white background with 12px blur — a glass-effect top bar.

**Cards:** White background, light border, 8px radius, 32px padding, subtle shadow that deepens on hover. The hover shadow should transition at `--duration-normal`.

**Buttons:** 6px radius, horizontal padding of 24px, vertical padding of 12px, semibold Libre Franklin at `--text-sm`. Primary buttons use `--color-primary-800` background with white text. Secondary buttons use a white background with navy border and text. Gold accent buttons use `--color-accent-500` background with navy text.

**Form Inputs:** 6px radius, default border color, primary-700 focus ring, white background, 12px vertical / 16px horizontal padding.

---

## 9. Accessibility Requirements

Accessibility is not optional. The token system was audited and remediated in March 2026 to meet WCAG 2.1 AA standards. Consuming projects must observe these rules:

**Text contrast:** All text must achieve at least 4.5:1 contrast against its background (AA). Headings and large text (≥ 18px or ≥ 14px bold) require 3:1. The token system's text colors on white exceed these thresholds, but always verify contrast when combining non-standard foreground/background pairs.

**Gold as text:** Never use Accent 500 (#FFD200) as text on light backgrounds. Use Accent 700 (#806800) or darker.

**Focus indicators:** All interactive elements must show a visible focus ring. The default focus color is `--color-focus-ring` (gold, #FFD200), which provides strong visibility against the navy palette.

**Semantic status colors:** Use the 700-weight semantic colors for text/icon foregrounds and the 100-weight variants for backgrounds. These pairings were verified for AA compliance.

---

## 10. Voice and Tone (Brief)

The visual identity projects scholarly authority tempered by warmth. Communications should follow suit.

**Tone attributes:** Clear, direct, and precise. Confident without being showy. Willing to use technical language when warranted, but never jargon for its own sake.

**Writing conventions:** Active voice. Short paragraphs. Typographer's quotes. Minimal em dashes — prefer commas, semicolons, and colons when they serve. When em dashes are used, they should not have surrounding spaces.

**Register:** Professional but not corporate. The voice belongs to a person, not an institution. It can be warm, skeptical, or wry as context demands — but it is always precise.

---

## 11. What This Package Contains

| File | Purpose |
|---|---|
| `tokens.css` | Canonical design tokens (CSS custom properties) |
| `brand-guidelines.md` | This document — written reference for all brand decisions |
| `style-guide.html` | Live, browsable visual reference that renders the tokens |
| `DK-Brand-v2.potx` | PowerPoint template (EB Garamond headings, Concourse T3 body, brand color theme) |
| `palette-audit-2026-03-31.md` | WCAG accessibility audit and remediation report |

---

## 12. Dark Mode

A dark mode token set is scaffolded in `tokens.css` (section 9, currently commented out). When implemented, it should invert surfaces and adjust text colors while preserving the navy/gold identity. The dark mode stub maps primary-400 as the link color and uses neutral-900 as the base surface.

---

*These guidelines are version-controlled alongside the token system. When tokens change, update this document to match.*
