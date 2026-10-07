# Databricks brand contract

The palette and type are **fixed**. Everything in the deck flows through the
`:root` tokens in `assets/template.html`. Do not introduce colors outside this
list, and do not retune the hues to match another brand — this template is
`od.design_system.requires: false` precisely so the Databricks look is stable.

> These tokens are approximated from Databricks brand decks (the SEGA
> Kinesis→Zerobus deck among them). If you have the official Databricks brand
> token file, reconcile these values against it before external use.

## Palette

| Token | Hex | Role |
|-------|-----|------|
| `--navy` | `#1B3139` | Ink. Dark slide background; headings on light slides. |
| `--navy-deep` | `#0E2229` | Darker tonal shape on dividers. |
| `--navy-tint` | `#26424C` | Faint geometric shapes on dark slides. |
| `--lava` | `#FF3621` | **The** accent — Databricks red/orange. Emphasis, title shapes, arrows, subheads. |
| `--paper` | `#F9F7F4` | Light slide background (warm off-white, not pure white). |
| `--surface` | `#FFFFFF` | Cards and panels on light slides. |
| `--ink` | `#1B3139` | Body/heading text on light slides. |
| `--muted` | `#5A6872` | Secondary text. |
| `--border` | `#E4E1DB` | Hairlines, card and node borders. |
| `--green` | `#00A972` | Diagram semantics only: source/customer swimlane, GA pill, bullet dots. |
| `--amber` | `#FFAB00` | Diagram semantics only: third-party cloud swimlane. |
| `--code-bg` / `--code-fg` | `#0B1A21` / `#E8EDEF` | Code / notebook blocks. |

**Accent discipline:** lava appears **at most twice per slide**. Green and amber
are never decoration — they only encode meaning inside diagrams. A content slide
that isn't a diagram should show no green or amber.

## Surfaces

Two slide surfaces, set by a class on `.slide`:

- `.slide.dark` → navy background, white text. Use for the **title**, every
  **section divider**, and the **logo** slide.
- `.slide.light` → paper background, ink text. Use for **all content** slides.

Alternating a dark divider between light sections is what gives the deck its
rhythm. Never ship a bare `class="slide"`.

## Type

- Display + body: **DM Sans** (bold 700 for headings, 500 for subheads, 400
  body). Loaded via Google Fonts in the seed, with a system geometric-sans
  fallback so the deck still renders offline.
- Mono: **DM Mono** for eyebrows, metadata, and code.
- Headings are tight (`letter-spacing: -0.02em`), bold, and large. Subheads are
  lava, medium weight. Body is ink or muted.

## Logo

The seed ships an **inline-SVG approximation** of the databricks mark + wordmark
in `.db-logo`, and a small corner glyph (`.db-foot`) for content slides. The
databricks logo is a **trademark** — replace the approximation with the official
asset before any customer-facing or external use. Keep it top-left on the title
slide and bottom-left (glyph only) on content slides.

## Geometric motifs

- **Title slide:** a cluster of three solid lava shapes (triangle, circle,
  square) bottom-right (`.title-shapes`), plus a short lava rule under the title.
- **Section dividers:** faint navy tonal shapes (semicircles + a triangle,
  `.divider-shapes`) bleeding off the right edge. Low contrast — they are texture,
  not focus.

Keep motifs to these two places. Do not scatter shapes across content slides.
