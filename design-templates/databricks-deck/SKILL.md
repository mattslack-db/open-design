---
name: databricks-deck
en_name: "Databricks Brand Deck"
zh_name: "Databricks 品牌演示文稿"
description: |
  Build a single-file HTML presentation in the Databricks brand system: navy
  title and section-divider slides with the lava-red geometric shape cluster,
  off-white content slides, colored swimlane architecture diagrams, current-vs-future
  comparison tables, and dark code / notebook step slides. For technical sales decks,
  migration proposals, platform overviews, and solution walkthroughs.
  Trigger keywords: databricks deck, databricks presentation, lakehouse deck,
  databricks branded slides, migration proposal deck.
en_description: |
  Build a single-file HTML presentation in the Databricks brand system: navy
  title / divider slides with the lava-red shape cluster, off-white content slides,
  colored swimlane architecture diagrams, comparison tables, and dark code / notebook
  step slides. For technical sales decks, migration proposals, and platform overviews.
zh_description: |
  用 Databricks 品牌视觉制作单文件 HTML 演示：深蓝标题/分节页配熔岩红几何图形、
  米白内容页、彩色泳道架构图、现状对比表、以及深色代码/notebook 步骤页。
  适用于技术售前、迁移方案、平台概览与解决方案讲解。
tags:
  - "databricks"
  - "lakehouse"
  - "technical-deck"
  - "migration-proposal"
  - "architecture-diagram"
  - "html deck"
  - "html slides"
triggers:
  - "databricks deck"
  - "databricks presentation"
  - "lakehouse deck"
  - "databricks branded slides"
  - "migration proposal deck"
  - "Databricks Brand Deck"
  - "html deck"
  - "html slides"
od:
  mode: deck
  surface: web
  scenario: "technical-sales"
  category: "presentations"
  preview:
    type: html
    entry: index.html
  design_system:
    requires: false
  craft:
    requires: [typography, color, anti-ai-slop]
  speaker_notes: true
  example_prompt: "Create a Databricks-branded deck proposing a migration from a legacy ingestion stack to Databricks. First ask only for missing essentials: audience, the current architecture, the target architecture / phases, headline numbers (cost, throughput), and deadline. Then produce the slide plan, written slides using the Databricks brand archetypes, and a critic pass against the checklist."
  example_prompt_i18n:
    zh-CN: "用 Databricks 品牌模板做一份把现有架构迁移到 Databricks 的方案 deck。先只问缺失的关键信息：受众、现状架构、目标架构/阶段、关键数字（成本、吞吐）、截止时间，然后产出页面规划与成稿，并按清单自检。"
---

# Databricks Brand Deck

Produce a **single-file horizontal-swipe HTML deck** in the Databricks visual
system from the seed in `assets/template.html` and the archetype library in
`references/layouts.md`.

The look: navy (`#1B3139`) title and divider slides carrying the lava-red
(`#FF3621`) geometric shape cluster; off-white (`#F9F7F4`) content slides with a
single lava accent; green/amber reserved for diagram semantics (swimlanes, GA
pills, bullet dots). This is a corporate technical brand — restraint over flash.

## Resource map

```
databricks-deck/
├── SKILL.md             ← you're reading this
├── example.html         ← baked sample deck (gallery preview; also a worked reference)
├── assets/
│   └── template.html    ← seed: brand :root tokens + every archetype class + proven nav (READ FIRST)
└── references/
    ├── brand.md         ← the brand contract: palette, type, logo, do / don't
    ├── layouts.md       ← the 11 paste-ready slide archetypes + theme-rhythm rules
    └── checklist.md     ← P0 / P1 / P2 self-review
```

## Workflow

### Step 0 — Pre-flight (read before writing any HTML)

1. **Read `assets/template.html`** end-to-end, through the `<style>` block AND
   the `<script>` block. The script solves iframe-specific nav bugs and keeps
   `.slide.active` + the dot row in sync — **do not rewrite it**.
2. **Read `references/brand.md`** — the palette and type are fixed. Do not
   introduce colors outside the `:root` tokens.
3. **Read `references/layouts.md`** — the 11 archetypes and the theme-rhythm
   rules. Every class the layouts use is already defined in the seed; if one is
   missing, add it to the seed's `<style>` rather than inlining it per slide.

> This template is **brand-locked**: `od.design_system.requires: false`, so no
> active design system is composed in. The Databricks tokens in the seed ARE the
> design system. Do not swap the palette to match another brand.

### Step 1 — Resolve intent

If the user already gave a complete outline, skip to Step 2. Otherwise infer
from the brief, and ask only the unresolved essentials in **one** consolidated
`<question-form>` — never one at a time:

| # | Question | Why |
|---|----------|-----|
| 1 | Audience & setting (customer exec / technical eval / internal) | language + depth |
| 2 | Current-state architecture (components, pain) | drives the swimlane + problem slides |
| 3 | Target architecture / phases | drives the phase dividers + phase diagrams |
| 4 | Headline numbers (cost, throughput, latency, savings) | the proof the deck must carry |
| 5 | Slide count / talk length | 10 min ≈ 8–10 · 20–30 min ≈ 14–18 |
| 6 | Hard constraints (must include / must not show) | avoids rework |

### Step 2 — Copy the seed + plan the rhythm BEFORE writing slides

Copy `assets/template.html` to the project root as `index.html`. Replace the
`<title>` and grep for `[REPLACE]` so no placeholder ships.

Then write the slide plan (archetype + theme per slide) before any content. A
healthy Databricks deck:

```
01  dark   title             ← lava shape cluster
02  light  bullets-timeline / content-cards   ← what the platform does
03  dark   section-divider   "Current state"
04  light  problem-row + swimlane-arch         ← the current architecture + its pain
05  dark   section-divider   "Phase 1"
06  light  bullets-timeline + swimlane-arch    ← the target state, annotated
07  light  comparison-table  "Qualification"   ← current vs. future
08  dark   logo-only / divider "Next steps"
09  light  dash-list         next steps
10  light  code-step ×N      "Step 1: Create table" …
```

Rules: a theme on every slide (`dark` | `light`); dark dividers separate
sections; no 3+ light slides without a dark breath; open on `dark` title, and
use a `dark` divider for each phase/section.

### Step 3 — Paste archetypes and fill

For each planned slide, copy the matching `<section>` from `references/layouts.md`
into the body, in order. Replace bracketed text with **real, specific copy — no
lorem, no filler**. Tag each slide `data-screen-label="01 Title"`, `"02 …"` in
order. Keep the `db-foot` glyph on content slides and the `db-logo corner` on the
title slide.

Diagram slides (`swimlane-arch`) carry meaning in color: green = source/customer
lane, amber = third-party cloud lane, lava = Databricks lane. Keep arrows lava.

### Step 4 — Secondary output for export

After `index.html` is complete, also write `slides.json` — an ordered array of
`{ "label", "archetype", "title", "body" }` objects, one per slide — so the deck
PPTX export has structured content to consume.

### Step 5 — Self-check

Run `references/checklist.md`. The P0 items (one accent per slide, theme on every
slide, brand colors only, logo placement, no placeholder text) must all pass:

```bash
grep 'class="slide' index.html   # confirm every slide has light|dark and the rhythm is sane
grep -n '\[REPLACE\]' index.html  # must return nothing
```

### Step 6 — Write the project file

Write the finished deck to `index.html`. Send one short assistant summary naming
`index.html` and describing the deck. **Do not** paste the full HTML source in
chat or emit a source-code `<artifact>` block — this is a filesystem runtime.

## Hard rules

- **Brand-locked palette.** Only the `:root` tokens. No off-brand hex values.
- **One accent (lava) per slide**, used at most twice. Green/amber only carry
  diagram semantics (swimlanes, GA pills, bullet dots) — never as decoration.
- **Theme class on every slide** (`dark` | `light`). Bare `class="slide"` is a regression.
- **Dark title + dark section dividers.** Open dark; break each section with a dark divider.
- **Don't rewrite the nav script.** It's proven and keeps `.slide.active` in sync.
- **No `scrollIntoView()`** — it breaks the iframe preview.
- **`data-screen-label` on every slide.**
- **The databricks wordmark is a trademark.** The seed ships an inline-SVG
  approximation in a clearly-marked slot; replace it with the official asset
  before any external use.

## Core principles

1. **Restraint over flash** — structure, large type, and whitespace carry the
   slide; no drop shadows, no gradients beyond the brand, no clip-art.
2. **Color is meaning** — lava is emphasis; green/amber are diagram roles.
3. **One idea per slide** — if a slide feels crowded, split it or pick a
   different archetype.
4. **Numbers are the proof** — put the headline figure where the eye lands.
