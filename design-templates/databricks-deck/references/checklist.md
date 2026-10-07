# Self-review checklist

Run top-to-bottom after generating. **P0 must all pass** before handoff.

## P0 — blocking

- [ ] **No placeholder text ships.** `grep -n '\[REPLACE\]\|\[TITLE\|\[Section' index.html` returns nothing.
- [ ] **Theme on every slide.** `grep 'class="slide' index.html` — every slide is `dark` or `light`; no bare `class="slide"`.
- [ ] **Brand colors only.** No hex outside the `:root` tokens. No off-brand accent.
- [ ] **One accent per slide**, used at most twice. Green/amber appear *only* in diagrams (swimlanes, GA pills, bullet dots) — never as decoration on a text slide.
- [ ] **Opens dark**, and each section is introduced by a **dark divider**.
- [ ] **Logo placement:** `db-logo corner` on the title slide, `db-foot` glyph on content slides.
- [ ] **Nav script untouched** and `.slide.active` toggles with keyboard, dots, and scroll.

## P1 — should fix

- [ ] No 3+ consecutive `light` slides without a `dark` breath.
- [ ] `data-screen-label="NN …"` on every slide, numbered in order.
- [ ] Headings are DM Sans bold; subheads are lava; body is ink/muted.
- [ ] Swimlane color is semantic: green = source/customer, amber = third-party cloud, lava = Databricks + arrows.
- [ ] Code blocks use the dark `.code` surface with `cm`/`kw`/`st`/`fn` spans, not raw text.
- [ ] `slides.json` written, one entry per slide, same order as the HTML.

## P2 — polish

- [ ] Tables: dark header row, green `.hl` only on the cell that earns emphasis.
- [ ] Title shapes and divider shapes appear only on title/divider slides, nowhere else.
- [ ] Numbers (cost, throughput, savings) land where the eye goes first.
- [ ] Official databricks logo asset swapped in if the deck is customer-facing.

## Rhythm spot-check

```bash
grep 'class="slide' index.html
```

Read the theme sequence. If you see `light × 4` in a row, promote one to a `dark`
divider. An 8+ slide deck with no `dark` slide after the title reads flat — add
section dividers.
