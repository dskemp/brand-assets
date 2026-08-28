# Changelog

## 2026-05-26

### Substantive
- **Created `DK-Brand-v2-systemfonts.potx`, a portable companion to `DK-Brand-v2.potx` that swaps every custom typeface for a web-safe system font.** The canonical template uses EB Garamond (with Medium and SemiBold variants) for headings and Concourse T3 for body, neither of which is preinstalled on most Windows, Mac, or web-PowerPoint environments. Without font embedding the canonical deck silently substitutes to whatever sans-serif the host system supplies for both faces, which is exactly what was happening on shared decks. The new file replaces EB Garamond and its variants with Georgia and Concourse T3 with Verdana; the choice of Verdana follows Matthew Butterick’s assessment in *Practical Typography* that Verdana (Matthew Carter, designed for screen) is among the few system sans-serifs worth using, and it shares a designer with Georgia. The notes-master theme’s Aptos and Aptos Display references were also swapped to Georgia and Verdana so notes pages render consistently on older Office installs.

### Technical
- **Set `b="1"` on every run-property element (`rPr`, `endParaRPr`, `defRPr`) that previously named EB Garamond Medium or SemiBold,** so the bold attribute now carries the weight gradation that the named-weight typeface strings used to convey. 54 bold flips total across 17 slide layouts, 1 slide master, and 1 slide; 215 typeface-string substitutions across `theme1.xml`, `theme2.xml`, every slide layout, the slide master, and the seeded title slide. Updated `docProps/app.xml`’s “Fonts Used” metadata to list the three actual typefaces now present (Arial, Georgia, Verdana) and reduced the `TitlesOfParts` vector size from 7 to 5 to match. Repackaged with `[Content_Types].xml` as the first archive entry per OOXML convention; content type preserved as `presentationml.template.main+xml`.
- **Validation.** All 29 XML parts parse cleanly; all 22 `.rels` files parse cleanly; all 48 relationships resolve to existing parts; ZIP integrity check passes; round-trip read-and-save via python-pptx succeeds; LibreOffice converts the file to PDF without errors and renders the seeded title slide in Georgia bold as expected.

## 2026-05-24 (eighth revision)

### Substantive
- **Synced the color scheme across `DK Brand.thmx` and `DK-Brand-v2.potx` to the canonical `DK Brand.xml`.** Both companion files previously embedded older accent assignments that drifted from the standalone color scheme. In `DK Brand.thmx`, `accent4` moved from `#4A5568` (gray) to `#AD4E2D` (extend-terracotta) and `accent6` from `#6B5B73` (slate) to `#4A7C59` (extend-sage). The `.potx` had drifted further — its `accent5` was `#CBD5E0` (neutral-300, light gray) and `accent6` was `#718096` (neutral-600, gray), neither of which appeared anywhere else in the brand system. The full reconciliation set the .potx accents to navy / gold / mid-blue / terracotta / teal / sage (matching the canonical .xml) and updated `folHlink` from `#4A5568` to `#2B4FA3` so the followed-link color sits in the primary blue family rather than reading as gray. After this revision, all three files (`.xml`, `.thmx`, `.potx`) carry the same twelve color slots, with every value traceable to a token in `tokens.css`.

### Changed
- **Switched the “Key Takeaways” headings on the Three Key Points layout from Concourse T3 to EB Garamond SemiBold.** The `Point label - 1`, `Point label - 2`, and `Point label - 3` placeholders on `slideLayout15.xml` previously used `Concourse T3` at 14pt with `b="1"`, which produced a synthesized-bold sans heading that read as a different typographic system from the rest of the deck (where headings are EB Garamond throughout). Replaced with `EB Garamond SemiBold` 14pt and explicitly cleared the bold attribute (`b="0"`) per the fifth-revision convention (use the named weight, not the synthesized bold). Affected 15 `defRPr` entries (3 shapes × 5 paragraph levels each) and 15 corresponding `b` attribute changes. The smaller `Point body` text on the same layout remains Concourse T3 (it is body text, not a heading, and the user’s heading-only change does not extend to it).
- **Demoted EB Garamond Medium to EB Garamond (Regular) on every non-heading placeholder.** Body and decorative uses of `EB Garamond Medium` reverted to the base Regular weight (typeface `EB Garamond`, with `pitchFamily="2" charset="0"`). Affected shapes: `Quote body` on `slideLayout9.xml` (lvl1 paragraph; deeper levels were already SemiBold italic for the attribution lines and were left alone), `Quote glyph` on `slideLayout9.xml` (the 120pt decorative curly opening quote), `Poll question` on `slideLayout10.xml` (lvl1 paragraph plus matching deeper-level defaults), `Question glyph` on `slideLayout10.xml` (the 120pt decorative question mark), and the `Prompt` body on `slideLayout14.xml` (Discussion Slide). Title, Section title, Caption title, Heading - left/right, Header label - A/B, and Row Label 1–4 placeholders kept `EB Garamond Medium` because the change rule explicitly governed non-headings only. Net: 15 Medium references became Regular; 22 Medium references remain (all on heading-class placeholders).

### Technical
- **Repackaged both archives with `[Content_Types].xml` first and a fixed UTC timestamp** so the resulting `.thmx` and `.potx` are byte-deterministic across runs. Verified by re-unzipping and parsing the embedded theme XML; the smoke test with `python-pptx` confirms the `.potx` carries the correct content type `presentationml.template.main+xml` (the library’s refusal to open templates directly is a library limitation, not a file defect).

### Open question
- **Whether to extend the “Regular for non-headings” rule beyond Medium.** Inside `Quote body`, the lvl2–lvl5 paragraph levels are currently `EB Garamond SemiBold` italic (the attribution and source lines). Those were never Medium and were left as-is under a literal reading of the change request. If the intent is broader — every non-heading body run should be Regular regardless of current weight — that is a separate sweep that would touch the Quote attribution lines and possibly inline-emphasis spans elsewhere. Flagged for the next revision.

## 2026-05-24 (seventh revision)

### Substantive
- **Reassigned two accent slots in `DK Brand.xml` for chromatic variety.** Swapped `accent4` from `#4A5568` (neutral-700 dark gray) to `#AD4E2D` (extend-terracotta), and `accent6` from `#6B5B73` (extend-slate) to `#4A7C59` (extend-sage). Both new values are drawn from `tokens.css` §1e (extended palette) and pass WCAG AA on white. Rationale: the prior `accent4` duplicated the grayscale already covered by `dk1` (`#2D3748`) and `dk2` (`#002959`), and the prior `accent6` was a desaturated slate that read as another gray on slides. Result: the six theme accents now cover six distinct hues — navy, gold, mid-blue, terracotta, teal, sage — giving 7–10-color slides (boxes, diagrams, comparison grids) enough chromatic range without leaving the canonical token system. PowerPoint's auto-generated tint/shade columns under each accent supply the lighter desaturated variants typically used as backgrounds for text boxes; the saturated accent stays accessible at the top of each picker column.
- **Note on the OOXML 6-accent ceiling.** The `<a:clrScheme>` element is hard-capped at six accents by the OOXML spec, so a literal expansion beyond six is not possible inside `DK Brand.xml`. The companion files (`DK Brand.thmx`, `DK-Brand-v2.potx`) can hold a `custClrLst` block at the `<a:theme>` level to expose additional "Custom Colors" in the PowerPoint picker; not added in this revision per scope.

## 2026-05-24 (sixth revision)

### Technical
- **Renamed every shape in every layout with a short descriptive name.** 121 shape renames across all 17 layouts and the slide master. Replaces generic names like `Shape 0`, `Shape 2`, `Text Placeholder 16` with role-based names (`Top navy hairline`, `Title underline`, `Content card`, `Content card left edge`, `Heading bar - left`, `Point circle - 1`, `Quote glyph`, `Question glyph`, `Background ellipse`, `Caption band`, `Image-caption separator`, `Row separator - 1`, `Header bar - A`, `Column rule`, `Instructions eyebrow`, etc.). Naming convention is sentence case with hyphenated suffixes only where the layout has more than one of the same role (e.g., `Content card - left` / `Content card - right` on the Two Column layouts; single-card layouts use `Content card` with no suffix). Slide-number placeholders are uniformly `Slide number`; title placeholders are `Title` (except Section Divider’s `Section title` and Full Bleed Image with Caption’s `Caption title`).
- **Confirmed all drop shadows are still in place.** Eleven shadows total, one on each white content card across Agenda, Single Content Block, Two Column, Two Column with Headings, Text + Image, Image + Text, and the three Point cards on Three Key Points. No shadows were dropped during any of the prior transformation passes.

## 2026-05-24 (fifth revision)

### Changed
- **Toned down every heavy-weight EB Garamond reference to SemiBold.** Across the user-reordered template, sixteen runs were set to `EB Garamond ExtraBold`, eight on Two Column with Headings, four on Full Bleed Image with Caption, and four on Quote. All were swapped to `EB Garamond SemiBold` with the bold attribute explicitly cleared (`b="0"`) so PowerPoint does not synthesize a bold-on-top-of-named-weight rendering. Body uses of `EB Garamond Medium` were left as-is; Medium sits a weight step below SemiBold and reads correctly on slides. Updated `brand-guidelines.md` §2.5 with the explicit weight rule (never heavier than SemiBold; set the typeface name rather than using `b="1"`).

## 2026-05-24 (fourth revision)

### Substantive
- **Three new slide layouts.**
  - **Title Only** (layout 15): light gray ground, top navy hairline, title placeholder with the gold-tab underline, and an empty stage below. Use for branded but free-form slides where the content varies and no card wrapper is wanted.
  - **Agenda** (layout 16): Single Content Block variant with auto-numbered bullets (1., 2., 3., …) at 24pt for session overviews.
  - **Comparison Grid** (layout 17): title at top, two navy header bars across columns A and B, a left-most label column, and four body rows with thin gray separators. Designed for case comparisons, doctrine vs. application, plaintiff vs. defendant tables.
- **Reimagined the Discussion Slide** (layout 12) as a horizontal split. The prompt now sits in a wider left column (~60 % of the slide) in EB Garamond 24pt, and the instructions sit in a narrower right column (~35 %) under a small gold “INSTRUCTIONS” eyebrow in Concourse T3 spaced caps. A thin vertical gold rule separates the two columns. The earlier stacked layout left a large dead zone below short prompts; the horizontal split makes the slide read as one composition regardless of prompt length.

### Changed
- **Quote body switched from roman to italic** at 22 pt. EB Garamond Roman at 22 pt on a navy ground still read as heavy; italic at the same size feels lighter and reads as a proper editorial pull-quote. Poll stays roman so the question reads as a direct prompt — the two layouts otherwise remain visual siblings (same body size, same glyph treatment, same gold-rule position).

## 2026-05-24 (third revision)

### Fixed
- **Slide-number placeholders inherit the master’s 12pt size.** The body step-down pass had been stamping its layout-specific size onto slide-number placeholders as well, producing 16pt to 24pt page numbers depending on layout. Updated the transform to skip sldNum placeholders so they fall through to the master’s 12pt default.
- **Quote and Poll layouts aligned to read as siblings.** Set both decorative glyphs (the curly opening quote and the question mark, at 120pt, 70 % alpha gold) to regular weight; previously both were bold, with the curly quote in particular reading as a heavy slab. Unified both body lvl 1 to 22pt EB Garamond regular with the standard step-down (22 / 16 / 14 / 12 / 12). Moved the gold rule to the same position on both (x = 1.50 in, y = 3.55 in, w = 1.80 in). Repositioned Quote’s attribution placeholder from y = 4.00 in to y = 3.80 in and source from y = 4.35 in to y = 4.15 in so the secondary block sits at the same vertical anchor as Poll’s instructions block.
- **Tightened the orphan-shape predicate so it catches small-but-not-zero shapes.** The earlier predicate checked for cx = 0 / cy = 0, but at least one orphan parked at (-100000, -100000) had cx = cy = 1 EMU and slipped through. Now treats anything ≤ 1000 EMU as orphan and removes the lingering 1 × 1 EMU rectangle on the Poll layout.
- **Moved the Discussion Slide instructions placeholder up.** Was at y = 4.10 in, leaving a large dead zone between a short prompt and the instructions line. Now at y = 3.40 in. Long prompts still wrap into the available space.

### Changed
- **Tightened body space-after rhythm from 80 % of font size to 60 %.** Previously, a 24 pt bullet produced 19.2 pt of trailing space; now it produces 14.4 pt. Reads tighter without becoming cramped; better with five or more bullets. Updated `brand-guidelines.md` §2.5 to match.

## 2026-05-24 (revision)

### Fixed
- **Restored alpha (transparency) on the decorative ellipses and glyphs in `DK-Brand-v2.potx`.** The earlier color-token swap on this date dropped the `<a:alpha>` child element when replacing `<a:srgbClr>` with `<a:schemeClr>`. That removed the 40 % opacity on the mid-blue ellipses behind Title Slide, Section Divider, and Thank You; the 45 % opacity on the Section Divider ellipse; and the 70 % opacity on the oversized gold quote glyph (Quote layout) and question-mark glyph (Poll layout). Fixed the swap routine to preserve any nested children on color tokens (alpha, lumMod, satMod, tint, shade) and reran the full transform on the source.
- **Reverted the title-underline tab move and the title placeholder height bump on content layouts.** The earlier change moved the small gold tab from y = 0.80 in to y = 0.65 in and bumped each title placeholder’s height from 0.55 in to 0.65 in. That was wrong: all seven content-layout title placeholders use `anchor="b"` (text bottom-anchors), so the bigger placeholder pushed the title text down and the tab cut through the middle of the title. Restored both values to their originals; the tab now sits at the baseline of the bottom-anchored title text as a proper underline.
- **Restored the original title-weight hierarchy.** The earlier pass set every title to bold per a literal reading of `brand-guidelines.md` §2.5. The template’s actual design used bold only on hero, section, caption, and display titles (Title Slide, Section Divider, Full Bleed Image with Caption, Thank You); the seven working content titles were regular weight, where smaller serif reads more elegantly without weight. Restored regular weight on the content titles, kept bold on hero / section / caption / display, and updated §2.5 to describe the actual weight hierarchy.
- **Restored the picture placeholders inside the Three Key Points circles.** The earlier pass replaced the three picture placeholders inside the navy circles with white EB Garamond Bold numbers “1,” “2,” “3.” The workflow is to drop an icon into each circle per slide, which is why the originals were picture placeholders. Removed the number text shapes and left the picture placeholders untouched. The three small gold underlines beneath each circle stay removed (a separate, approved change from the prior pass).

## 2026-05-24

### Technical
- **Added standalone Office theme files.** Saved `DK Brand.thmx` and `DK Brand.xml` into the brand-assets folder so the DK Brand palette and theme are available across Word, Excel, and PowerPoint via the Office Themes and Theme Colors galleries. Fixed the .thmx font scheme on intake: it was named `"Test"` and used Concourse T4 for both major and minor fonts. Renamed the scheme to `"DK Brand"` and corrected the fonts to Georgia (major / heading, matching the .potx convention as a safe fallback for EB Garamond) and Concourse T3 (minor / body). The color scheme in both files was already conformant with `brand-guidelines.md` (navy + gold + neutrals + teal + slate, with hlink and folHlink in the primary-700 / primary-600 range) and required no edits.
- **Slide template hygiene pass on `DK-Brand-v2.potx`.** Reviewed all 14 layouts as a senior UI/UX critique and applied a consolidated change set. Reasoning: the slide-number placeholder overlapped the bottom gold bar on light layouts, gold accents were used too frequently to read as structural, line spacing was inconsistent across layouts, body text sizes did not step down by level, titles were not bold, and shape fills were hardcoded hex values rather than theme color slots. The pass:
  - Removed the full-width gold bar from the bottom of every layout that carried it (2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 13, 14). Resolves the slide-number overlap on the light content layouts.
  - Removed the top gold bar from the Discussion Slide (12) so it matches the dark-slide treatment used elsewhere.
  - Removed the short centered gold rule from the Title Slide (2) and Thank You (14); the navy background plus the bold serif title carries the hierarchy without it.
  - Removed the three small gold underlines beneath the circles on Three Key Points (13). Replaced the empty picture placeholders inside the circles with white EB Garamond Bold numbers “1,” “2,” “3” as a default visual.
  - Removed orphan zero-dimension shapes from layouts 8 and 12.
  - Moved the title-underline gold tab from y = 0.80 in to y = 0.65 in on all content layouts, and bumped the title placeholder height to 0.65 in so two-line titles do not collide with the tab.
  - Set every title placeholder to EB Garamond Bold. Held title sizes at the existing four-tier scale (content 30pt, caption 26pt, section 34pt, hero 38pt, display 42pt) and documented the scale in `brand-guidelines.md` §2.5.
  - Applied a single body size step-down across every body placeholder (default lvl1 20pt → lvl2 16pt → lvl3 14pt → lvl4–9 12pt; Single Content Block keeps a larger 24 / 20 / 16 run; Three Key Points stays 16 / 14 / 12). Brought the master body fallback down from 32pt at lvl1 to 20pt.
  - Switched line spacing to 110% for sans (Concourse T3) blocks and titles; 115% for the two large serif blocks (Quote body at 22pt and Discussion prompt at 26pt). Set space-after to 80% of the font size on every body placeholder and space-before to 0.
  - Switched the Discussion Slide body lvl 2–5 from EB Garamond to Concourse T3 so instructional text reads as instructional. Lvl 1 (the prompt) stays serif.
  - Switched the Three Key Points per-column point labels from EB Garamond to Concourse T3 Bold at 14pt.
  - Replaced literal hex fills (`#002959`, `#FFD200`, `#F5F6F7`, `#FFFFFF`, `#1E3A8A`) with their scheme color references (`accent1`, `accent2`, `bg2`, `bg1`, `accent3`). PowerPoint’s **Design → Variants → Colors** menu will now recolor every accent in a single step; the visual output is identical to the prior hex values.
- Updated `brand-guidelines.md` §2.5 to describe the title scale, body step-down, line spacing rules, space-after rule, and the constrained role of the gold accent in the slide template.

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
