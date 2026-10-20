---
name: infographic
description: Use when the user asks for an infographic, one-pager, visual summary, interactive explainer, report page, process/timeline/architecture/org diagram, HTML slide deck / presentation, or "make this visual" as an HTML file — or wants a new page matching the Advanced Perception / awareAI / Yunex Traffic house style of the existing infographics.
---

# House-Style HTML Infographics

## Overview

Every infographic is **one self-contained `.html` file** built with Tailwind (Play CDN), Inter + JetBrains Mono, a slate neutral base, fixed semantic accent colors, Lucide icons and (optionally) Chart.js. New pages must look like siblings of the reference files in `examples/` — same header, cards, badges, typography and color meaning — while the *content* comes strictly from the user.

Files in this skill:
- `references/design-system.md` — tokens: stack, typography, colors, shapes, icons, charts, dark theme, motion. **Read fully before writing.**
- `references/components.md` — copy-paste component snippets + interactive JS patterns. Read the sections you need.
- `assets/template.html` — starting skeleton. Always start from a copy of it.
- `../../examples/*.html` — the reference infographics (plugin root). Skim the one matching your archetype for composition; take tokens from design-system.md, not from the examples (they contain the mistakes listed under Gotchas).

## Workflow

1. **Understand the content.** Extract from the user's material: title, audience, the 1–3 key messages, every number (with unit and whether it is measured or estimated), entities, steps/phases, comparisons. If key facts are missing, ask; do not fill gaps with invented data.
2. **Pick an archetype** (table below). Mixed content → the archetype of the main message; use tabs (components §17) when there are more than ~4 distinct sections.
3. **Copy `assets/template.html`** to `<topic>_infographic.html` (snake_case) in the user's target folder; fill the `{{…}}` placeholders. Drop the Chart.js `<script>` and theme block if there are no charts.
4. **Compose** `<main>` from components.md snippets. Order: headline message → evidence (KPIs, charts, flows) → detail (tables, cards) → formal summary / footnotes. Wrap each topic in `<section data-slide="Short title">` — see "View modes" below.
5. **Wire interactivity** only where it adds understanding (step detail, filtering, simulation). Data lives in the `DATA` const; render from it.
6. **Verify** with the checklist below, then open the file (`open <file>` on macOS) or screenshot it if a browser tool is available and fix anything off.

## Archetypes

| Archetype | Use for | Skeleton (top → bottom) | Reference |
|---|---|---|---|
| **Report / Benchmark** | measurements, A-vs-B, SLA, results | hero with verdict if there is one (2) → KPI cards, one per compared item (3) → 2-col chart cards (4, 14b) → step flow if the test has a pipeline (7) → data table (9) → formal summary (15) | `camera_latency_performance_report_infographic.html` |
| **Anatomy / Spec** | formats, naming schemes, structures, standards | centered hero (2) → `rounded-3xl` board with big solid segment tiles + tinted segment cards (8) + rule ribbons (12) → comparison gradient cards (14) → generator/decoder (13, 23) | `hostname_and_serial_number_infographic.html` |
| **Process Explainer (tabbed)** | release processes, SDLC, policies, playbooks | header with tabs (17) → Overview: hero + feature cards (5) + stat strip (6) → taxonomy cards (8) → stepper + detail (18) → strategy lists (11) → simulator (23) | `awareai_release_process_infographic.html`, `ai_native_sdlc_infographics.html` |
| **Diagram / Timeline** | roadmaps, milestones, org structures, architectures | HUD legend + filter pills (24) over a diagram; click → inspector drawer (19). Prefer HTML/SVG grids; use `<canvas>` with pan/zoom only for >20 nodes | `awareai_hw_2_0_timeline_infographic.html`, `ai_native_sdlc_org_structure.html` |
| **Ops Blueprint (dark)** | AI copilots, telemetry, live systems, integration topologies | dark theme; hero + stat strip → SVG topology with animated flow lines next to a terminal/chat panel (13) → phase cards → capability cards | `dmp_ai_operations_lifecycle_copilot_infographic.html` |

Default theme is **light**. Use dark only for the Ops Blueprint archetype or on request.

## View modes: Article and Slides

Every page supports two modes, switched in the header (the "Deck" CSS/JS blocks in the template — never edit them):
- **Article** — the normal scrolling page.
- **Slides** — one slide at a time, a left panel with numbered thumbnails of all slides, a bottom bar with progress, clickable slide titles (truncated; when they don't all fit, the bar shows those around the current slide and a `^` button opens a list of all slides) and prev/next, `←`/`→` (also PageUp/PageDown, Home/End) and swipe. `#slide-3` in the URL opens slide 3. Print in slides mode puts one slide per page.

Start mode is `<body data-mode="article">`; set `data-mode="slides"` when the user asks for a presentation, deck or slides.

**Splitting content into slides** (always do it, even when the user only wants an article):
- Every top-level block of `<main>` is a `<section data-slide="Title">`. Content outside a slide is hidden in slides mode. Slides must not be nested.
- One topic / one key message per slide, sized to roughly one screen (~1280×720): hero = slide 1; a KPI row; one or two chart cards; one flow; one table; formal summary last. Split long tables, card grids or step lists by logical group ("Phases 1–3", "Phases 4–6"); merge tiny related blocks (a callout belongs to the chart it explains).
- Titles are 1–4 words, distinct, and read as an outline in the panel ("Verdict", "Latency per camera", "Test setup").
- If the user dictates the split ("split this into two slides", "put X and Y on one slide"), follow it exactly over these heuristics.
- Tabs (components §17): put `article-only` on the tab `<nav>`; each `data-panel` wrapper holds one or more slides. In slides mode the panels are flattened and the tab names become group labels in the panel. Keep `switchTab` a global function.
- Drawers, modals and toasts go outside `<main>` (they are page-level, not slides).

## Rules

**Content integrity**
- Every number, name, date and claim comes from the user's input. Never invent metrics, percentages, vendors or quotes to fill a card. If a layout slot has no data, remove the slot.
- Label provenance (design-system.md "Provenance badges"): `Measured`, `Estimated`, `Derived`, `Quoted`. Derived numbers show their formula (components §15) or a footnote.
- Compared items get colors by verdict (design-system.md "Assigning colors to compared items").
- Units always attached, in mono: `790 ms`, `16 GB`, `2× / year`.

**Visual consistency**
- Only tokens from design-system.md: `slate` neutrals, semantic accents with fixed meaning (emerald = good, amber = warning/estimate, rose = bad, sky/blue = primary/info), categorical order for series.
- One accent per item, used consistently for that item everywhere (card, chart series, badge, legend).
- Numbers/IDs/dates/units in `font-mono`; prose in Inter.
- Lucide icons only — no emoji icons, no hand-drawn SVG icons unless Lucide lacks the concept. Exception: the header title icon is always the Yunex brand-mark SVG from the template (transparent, no tile or shadow, left corners rounded via its clipPath); never replace it with a Lucide icon, wrap it in a tile, or recolor it.

**Engineering**
- One file, CDN scripts pinned exactly as in the template, no other dependencies, works from `file://`.
- Responsive: single column on mobile, grids from `sm:`/`md:`/`lg:`. Check that no grid has more columns than items.
- Tailwind Play CDN only sees complete class names: in JS write full literals (`'bg-emerald-50 text-emerald-700'`), never build them like `` `bg-${c}-50` ``.
- `lucide.createIcons()` after every DOM render. Use `textContent` or `escapeHtml()` for data inserted into HTML.
- Print: header has Export/Print; nothing essential hidden behind hover-only states.

## Verification checklist

- [ ] Head matches template (pinned CDNs, Inter + JetBrains Mono, tailwind.config fonts)
- [ ] Header: Yunex brand-mark tile copied unchanged from the template, eyebrow badge, mono meta, h1; footer present
- [ ] Every number traceable to the user's input; estimates labeled
- [ ] Only `slate` neutrals; accent meanings respected; same entity = same color everywhere
- [ ] No invalid Tailwind classes (see Gotchas); no console errors; icons render
- [ ] Layout checked at mobile and desktop widths
- [ ] Every block of `<main>` is a titled `data-slide`; slides mode checked (each slide fits/reads on its own, thumbnails render, `←`/`→` work)
- [ ] Charts: house defaults applied, units in ticks/tooltips, thresholds visible

## Gotchas (seen in the Gemini-generated references — do not copy)

| Mistake | Fix |
|---|---|
| `shadow-xs`, `text-3.5xl`, `border-slate-150`, `text-slate-2001` | Not Tailwind v3 classes — use `shadow-sm`, `text-3xl`/`text-4xl`, `border-slate-100`/`200` |
| `animate-fadeIn` (undefined) | Use `transition` + opacity classes, or omit |
| `lucide@latest`, unpinned `chart.js` | Pin versions as in template |
| Mixing Inter and Plus Jakarta Sans across files | Inter only |
| `red-*` and `rose-*` mixed in one page | Pick `rose` for negatives |
| Emoji used as icons (🖥️ 📷) | Lucide icon |
| Filling a stat strip with plausible-looking figures not in the source | Only user-provided figures; drop the strip otherwise |
| `innerHTML` with raw data strings | `textContent` / `escapeHtml()` |
| `user-scalable=no`, `select-none` on body | Keep default viewport and text selection |
