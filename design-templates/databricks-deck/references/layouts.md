# Slide archetypes

Eleven paste-ready `<section>` blocks. Copy the one you need into the body of
your `index.html` (copied from `assets/template.html`), then replace the
bracketed text. **Every class here is already defined in the seed's `<style>`** —
if you need a tweak, adjust the seed's CSS, don't invent inline class names.

Theme on every slide: `dark` for title / dividers / logo, `light` for content.
Keep the `db-foot` glyph on content slides.

---

## Theme rhythm (plan before writing)

- Open on a **dark title** (1), break every section with a **dark divider**.
- No 3+ consecutive light slides without a dark breath.
- Dividers map to the deck's sections ("Current state", "Phase 1", "Next steps").
- Diagram color is semantic: green = source/customer lane, amber = third-party
  cloud lane, lava = Databricks lane + all arrows.

---

## 1 · Title (dark)

```html
<section class="slide dark" data-screen-label="01 Title">
  <div class="db-logo corner">
    <svg class="mark" viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg>
    <span class="word">databricks</span>
  </div>
  <h1 class="h-hero">[TITLE line one:<br/>line two]</h1>
  <hr class="accent-rule" />
  <div class="title-shapes"><span class="tr"></span><span class="ci"></span><span class="sq"></span></div>
</section>
```

## 2 · Section divider (dark)

```html
<section class="slide dark" data-screen-label="03 Current state">
  <h2 class="h-hero">[Section name]</h2>
  <div class="divider-shapes"><span class="semi a"></span><span class="semi b"></span><span class="tri"></span></div>
</section>
```

## 3 · Logo only (dark)

```html
<section class="slide dark center" data-screen-label="12 Logo">
  <div class="db-logo">
    <svg class="mark" viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg>
    <span class="word">databricks</span>
  </div>
</section>
```

## 4 · Content + card stack (light)

Left: icon + heading + lava subtext. Right: stacked labeled cards, one highlighted.

```html
<section class="slide light" data-screen-label="02 Platform">
  <div class="split">
    <div>
      <div class="aside-icon"><svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="2"><path d="M24 6l16 9v18l-16 9-16-9V15z"/></svg></div>
      <h2 class="h-md">[Lakeflow]</h2>
      <p class="subhead">[Unified, intelligent solution for data engineering]</p>
    </div>
    <div class="card-stack">
      <div class="card is-highlight">
        <span class="card-tab">[Ingest]</span>
        <span class="card-icon"><svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="2"><circle cx="24" cy="24" r="16"/></svg></span>
        <h3 class="card-title">[Connect]</h3>
        <p class="card-desc">[Efficient data ingestion into your lakehouse]</p>
      </div>
      <div class="card">
        <span class="card-tab">[Transform]</span>
        <span class="card-icon"><svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="2"><path d="M8 24h32M24 8v32"/></svg></span>
        <h3 class="card-title">[Declarative Pipelines]</h3>
        <p class="card-desc">[Reliable data pipelines made easy]</p>
      </div>
      <div class="card">
        <span class="card-tab">[Orchestrate]</span>
        <span class="card-icon"><svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="2"><rect x="10" y="10" width="28" height="28" rx="4"/></svg></span>
        <h3 class="card-title">[Jobs]</h3>
        <p class="card-desc">[Orchestrate workflows across the platform]</p>
      </div>
    </div>
  </div>
  <div class="db-foot"><svg viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg></div>
</section>
```

## 5 · Feature + diagram panel (light)

Title + lava subhead, left body text, right dark panel, GA / CTA pills.

```html
<section class="slide light" data-screen-label="04 Zerobus">
  <h2 class="h-xl">[Zerobus Ingest]</h2>
  <p class="subhead">[Simplify ingestion for IoT, clickstream, telemetry]</p>
  <div class="feature">
    <div class="body">
      <p><strong>[Push event data directly to your Lakehouse, eliminating data hops.]</strong></p>
      <p><u>[Performance at scale]</u> [— near real-time writes (&lt; 5 sec), high throughput, built for concurrency.]</p>
      <div class="pills"><span class="pill ga">[GA]</span><span class="pill cta">[Just create a table → push data]</span></div>
    </div>
    <div class="panel">
      <p class="panel-title">[Zerobus Ingest]</p>
      <!-- a mini diagram, image, or node list goes here -->
      <p class="lead" style="color:rgba(255,255,255,.8)">[Producers → Zerobus → Unity Catalog]</p>
    </div>
  </div>
</section>
```

## 6 · Problem row — 3 icon columns (light)

```html
<section class="slide light" data-screen-label="05 Multi-hop">
  <h2 class="h-xl">[Multi-Hop Ingestion via Kinesis]</h2>
  <div class="icon-row">
    <div class="icon-col"><span class="ic"><svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="2"><path d="M24 6v28M14 20l10-10 10 10"/></svg></span><span class="pill-label">[Unnecessary architectural complexity]</span></div>
    <div class="icon-col"><span class="ic"><svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="2"><path d="M24 6l16 6v10c0 10-7 16-16 20-9-4-16-10-16-20V12z"/></svg></span><span class="pill-label">[AWS lock-in via Kinesis]</span></div>
    <div class="icon-col"><span class="ic"><svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="2"><path d="M10 38L30 18m-6-6l10 10"/></svg></span><span class="pill-label">[Additional infrastructure to maintain]</span></div>
  </div>
  <ul class="bullets">
    <li>[Game clients send telemetry via SDK to API Gateway]</li>
    <li>[API Gateway forwards to Amazon Kinesis]</li>
    <li>[Kinesis streams into the Bronze table]</li>
  </ul>
  <div class="db-foot"><svg viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg></div>
</section>
```

## 7 · Swimlane architecture diagram (light)

Colored lane headers + arrow-connected nodes. Color = meaning.

```html
<section class="slide light" data-screen-label="06 Current state">
  <h2 class="h-xl">[Current state]</h2>
  <div class="lanes">
    <span class="lane-head green">[SEGA]</span>
    <span class="lane-head amber">[AWS]</span>
    <span class="lane-head lava">[Databricks]</span>
  </div>
  <div class="arch">
    <span class="node edge-green">[Game<br/>Clients]</span>
    <span class="arrow">→</span>
    <span class="node edge-green">[Prism SDK<br/>telemetry]</span>
    <span class="arrow">→</span>
    <span class="node">[API Gateway]</span>
    <span class="arrow">→</span>
    <span class="node">[Amazon<br/>Kinesis]</span>
    <span class="arrow">→<span class="edge-note">[gRPC/REST]</span></span>
    <span class="node edge-lava">[Bronze]</span>
    <span class="node band">[Silver]</span>
    <span class="node band">[Gold]</span>
  </div>
  <div class="db-foot"><svg viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg></div>
</section>
```

## 8 · Bullets + timeline footer (light)

Green bullet dots, optional sub-bullets, lava `Timeline:` line.

```html
<section class="slide light" data-screen-label="07 Phase 1">
  <h2 class="h-xl">[API Gateway Writes to Zerobus]</h2>
  <p class="subhead">[Drop Kinesis, zero game-developer impact]</p>
  <ul class="bullets">
    <li>[Update API Gateway backend from Kinesis to the Zerobus REST endpoint]</li>
    <li>[Game clients and SDK remain completely unchanged]
      <ul class="sub"><li>[Immediate elimination of Kinesis ($6K/month savings)]</li></ul>
    </li>
    <li>[Reduced architecture: one fewer AWS component to manage]</li>
  </ul>
  <p class="timeline"><b>Timeline:</b> [Fastest path to value — backend config change only]</p>
  <div class="db-foot"><svg viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg></div>
</section>
```

## 9 · Dash list (light)

```html
<section class="slide light" data-screen-label="11 Next steps">
  <h2 class="h-xl">[Next steps]</h2>
  <ul class="dash-list">
    <li>[Discussion with Databricks team]</li>
    <li>[Agree on the phase]</li>
    <li>[Kick off evaluation]</li>
    <li>[Share results]</li>
    <li>[Approval and production deployment]</li>
  </ul>
  <div class="db-foot"><svg viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg></div>
</section>
```

## 10 · Comparison table (light)

Dark header row, current vs. future, optional green highlight cell.

```html
<section class="slide light" data-screen-label="10 Qualification">
  <h2 class="h-xl">[Qualification]</h2>
  <table class="cmp-table">
    <thead><tr><th>[Area]</th><th>[Current State]</th><th>[Future State]</th></tr></thead>
    <tbody>
      <tr><th>[Throughput]</th><td>[~30K events/sec, JSON payloads]</td><td>[Near real-time writes (&lt; 5 sec), high throughput]</td></tr>
      <tr><th>[Cost]</th><td>[Kinesis: ~$6K/month]</td><td>[Zerobus $0.050/GB <span class="hl">[Promo: 50% off until Sep 1, 2026]</span>]</td></tr>
      <tr><th>[Guarantees]</th><td>[At-least-once is sufficient]</td><td>[Confirmed viable]</td></tr>
    </tbody>
  </table>
  <div class="db-foot"><svg viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg></div>
</section>
```

## 11 · Code / notebook step (light)

Title + lava subhead ("Step N: …"), dark code block. Use `cm`/`kw`/`st`/`fn`
spans for comment / keyword / string / function coloring.

```html
<section class="slide light" data-screen-label="13 Step 1">
  <h2 class="h-xl">[Step 1: Create Table]</h2>
  <p class="subhead">[Create a managed Delta table in Unity Catalog]</p>
  <div class="code"><pre><span class="cm">%sql</span>
<span class="kw">CREATE TABLE</span> catalog.schema.events (
  id <span class="kw">INT</span>, payload <span class="kw">STRING</span>, name <span class="kw">STRING</span>
);</pre></div>
  <div class="db-foot"><svg viewBox="0 0 32 32" aria-hidden="true"><path d="M16 3 3 10l13 7 13-7-13-7Z" stroke="#FF3621" stroke-width="1.4" fill="none"/></svg></div>
</section>
```

---

### Pre-flight class list

Confirm these exist in the seed's `<style>` before writing (they do, out of the box):

`h-hero` · `h-xl` · `h-md` · `subhead` · `lead` · `eyebrow` · `accent-rule` ·
`db-logo` / `corner` / `mark` / `word` · `db-foot` · `title-shapes` (`tr`/`ci`/`sq`) ·
`divider-shapes` (`semi`/`tri`) · `split` · `aside-icon` · `card-stack` · `card` /
`is-highlight` / `card-tab` / `card-icon` / `card-title` / `card-desc` · `feature` /
`panel` / `panel-title` · `pills` / `pill` / `ga` / `cta` · `icon-row` / `icon-col` /
`ic` / `pill-label` · `lanes` / `lane-head` (`green`/`amber`/`lava`) · `arch` / `node`
(`edge-green`/`edge-lava`/`band`/`tag-lava`) / `arrow` / `edge-note` · `bullets` /
`sub` / `timeline` · `dash-list` · `cmp-table` / `hl` · `code` (`cm`/`kw`/`st`/`fn`).
