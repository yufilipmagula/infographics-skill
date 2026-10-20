# Design System — Tokens

Derived from the reference infographics in `examples/`. Everything is plain Tailwind v3 utility classes (Play CDN). Use these tokens exactly; do not invent new palettes, fonts or radii.

## 1. Stack (pinned)

```html
<script src="https://cdn.tailwindcss.com/3.4.16"></script>
<script src="https://unpkg.com/lucide@1.59.0/dist/umd/lucide.min.js"></script>          <!-- icons -->
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.5.1/dist/chart.umd.min.js"></script> <!-- only if charts -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
```

Tailwind config (always):

```js
tailwind.config = { theme: { extend: { fontFamily: {
  sans: ['Inter', 'sans-serif'],
  mono: ['"JetBrains Mono"', 'monospace'],
}}}}
```

No other libraries. No build step. One self-contained `.html` file.

## 2. Typography

| Role | Classes |
|---|---|
| Page title (header h1) | `text-lg sm:text-xl font-extrabold tracking-tight text-slate-900` |
| Hero / section title (h2) | `text-2xl sm:text-3xl font-extrabold tracking-tight text-slate-900` |
| Card title (h3) | `text-base font-bold text-slate-900` |
| Small card title (h4) | `text-sm font-bold text-slate-900` |
| Subtitle under a title | `text-xs text-slate-500` (`mt-0.5`) |
| Body | `text-sm text-slate-600 leading-relaxed` |
| Dense body (cards) | `text-xs text-slate-600 leading-relaxed` |
| Eyebrow / label | `text-[10px] sm:text-xs font-bold uppercase tracking-wider text-slate-400` |
| Mono eyebrow (step no., phase) | `text-[10px] font-mono font-bold uppercase tracking-wider text-slate-400` |
| Big KPI number | `text-4xl font-extrabold font-mono tracking-tight text-{accent}-600` |
| Medium stat | `text-2xl font-black font-mono text-slate-900` |
| Footnote | `text-[11px] text-slate-500` |
| Inline emphasis | `<strong class="text-slate-900">` |

**Mono (`font-mono`) is for:** numbers with units, IDs, versions, dates, file names, code, step numbers, unit chips, table headers. Everything else is `font-sans` (Inter).

Gradient headline accent (max one per page):
`<span class="bg-gradient-to-r from-sky-600 to-emerald-600 bg-clip-text text-transparent">…</span>`

## 3. Color

### Neutrals (Tailwind `slate` only — never `gray`/`zinc`/`neutral`)

| Use | Light theme | Dark theme |
|---|---|---|
| Page background | `bg-slate-50` | `bg-slate-950` |
| Card surface | `bg-white` | `bg-slate-900/80` |
| Inset / nested surface | `bg-slate-50` (`/70`) | `bg-slate-950/70` |
| Border | `border-slate-200` | `border-slate-800` |
| Inner divider | `border-slate-100` | `border-slate-800/60` |
| Heading text | `text-slate-900` | `text-white` |
| Body text | `text-slate-600` | `text-slate-300` |
| Muted text | `text-slate-500` / `-400` | `text-slate-400` / `-500` |
| Text base on `<body>` | `text-slate-800` | `text-slate-100` |

### Semantic accents (meaning is fixed — never swap)

| Meaning | Accent | Typical usage |
|---|---|---|
| Primary / info / selected / brand | `sky` (600) or `blue` (600) | active tab, primary button, info badge, links |
| Success / measured / pass / complete / current | `emerald` | "Measured", "Qualified", margin remaining, active milestone |
| Warning / estimate / budget / exception / transition | `amber` | "Estimated", SLA budget, hotfix, "needs action" |
| Danger / fail / over budget / blocked | `rose` (use `red` only if the user's brand demands; never mix both) | "Blocked", "+440 ms over" |
| Secondary categories | `violet`, `teal`, `cyan`, `indigo`, `orange` | phases, series, squads |

### Accent recipes (substitute `{c}` with the accent)

| Element | Light | Dark |
|---|---|---|
| Soft badge | `bg-{c}-50 text-{c}-700 border border-{c}-200` | `bg-{c}-500/10 text-{c}-400 border border-{c}-500/30` |
| Icon tile | `bg-{c}-50 border border-{c}-100 text-{c}-600` | `bg-{c}-500/10 border border-{c}-500/20 text-{c}-400` |
| Tinted card | `bg-{c}-50/60 border border-{c}-200/80` | `bg-{c}-950/30 border border-{c}-800/40` |
| Solid fill | `bg-{c}-500 text-white shadow-lg shadow-{c}-500/25` | same |
| Accent text | `text-{c}-600` (numbers), `text-{c}-700` (labels) | `text-{c}-400` |
| Top accent bar | `border-t-4 border-t-{c}-500` | same |
| Dot | `w-2 h-2 rounded-full bg-{c}-500` | `bg-{c}-400` |

### Categorical order (phases, series, segments)

Use in this order so consecutive items always contrast:

| # | Tailwind | Hex (for Chart.js / canvas / SVG) |
|---|---|---|
| 1 | sky-600 / blue-600 | `#0284c7` / `#2563eb` |
| 2 | emerald-500 | `#10b981` |
| 3 | violet-500 | `#8b5cf6` |
| 4 | amber-500 | `#f59e0b` |
| 5 | teal-500 | `#14b8a6` |
| 6 | rose-500 | `#f43f5e` |
| 7 | cyan-500 | `#06b6d4` |
| 8 | orange-500 | `#f97316` |

### Assigning colors to compared items (A vs B vs C)

1. Item that fails / is rejected → `rose`.
2. Item that is recommended / the winner → `emerald` (add a floating "Recommended" pill, components §7).
3. All other items → next colors from the categorical order, skipping any already used in steps 1–2.
4. With no verdict at all → pure categorical order.

The assignment is fixed for the whole page: KPI card, chart series, table column dot, legend.

### Provenance badges

| Label | Accent | Use |
|---|---|---|
| `Measured` | emerald | observed in a test / production |
| `Estimated` / `Projected` | amber | calculated forecasts, vendor specs applied to our case |
| `Derived` | slate (`bg-slate-100 text-slate-700 border-slate-200`) | arithmetic on given numbers (margins, deltas, %); show the formula |
| `Quoted` / `Spec` | sky | figures from a datasheet, offer or BOM |

Only label where provenance matters for the reader; one badge per KPI card, not per table cell.

Neutral hex values for canvas/SVG/Chart.js: slate-900 `#0f172a`, -800 `#1e293b`, -700 `#334155`, -600 `#475569`, -500 `#64748b`, -400 `#94a3b8`, -300 `#cbd5e1`, -200 `#e2e8f0`, -100 `#f1f5f9`, -50 `#f8fafc`.

## 4. Shape, depth, spacing

| Token | Value |
|---|---|
| Page container | `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` (narrow docs: `max-w-6xl`) |
| Vertical rhythm | `<main class="… py-8 space-y-8">` |
| Grid gaps | cards `gap-4`–`gap-6`, sections `gap-8` |
| Major card | `rounded-2xl p-6` (hero board: `rounded-3xl p-6 sm:p-10`) |
| Nested card / step | `rounded-xl p-4` |
| Inset / list row | `rounded-lg p-3` |
| Badges | `rounded` (square-ish) or `rounded-full` (pills) |
| Default shadow | `shadow-sm`, hover `hover:shadow-md transition` |
| Floating UI (drawer, toast, modal) | `shadow-2xl` |
| Hero board shadow | `shadow-xl shadow-slate-200/60` |
| Card footers | `mt-4 pt-3 border-t border-slate-100` |
| Body | `antialiased min-h-screen selection:bg-sky-600 selection:text-white` |

## 5. Iconography

**Brand mark (header title icon):** the Yunex SVG in `assets/template.html` (`h-11 w-auto`), placed directly in the header — no tile, no background, no shadow (transparent). The left bar's top-left and bottom-left corners are rounded by the SVG's own `clipPath`. Copy it exactly (viewBox, clipPath, gradient, path); it appears once per page, in both light and dark themes. The same mark is the favicon: a data-URI `<link rel="icon">` in the template `<head>` (square-padded viewBox) — copy it as is.

- Lucide only: `<i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600"></i>` and call `lucide.createIcons()` once after load **and again after every innerHTML render**.
- Sizes: inline `w-3.5 h-3.5`/`w-4 h-4`, tile `w-5 h-5` in `w-10 h-10 rounded-lg` tile, watermark `w-56 h-56 opacity-10`.
- Common picks: `check-circle-2` (pass), `x-circle` (fail), `alert-triangle` (warn), `alert-circle` (note), `info`, `shield` (security), `zap` (speed/AI), `clock` (cadence), `activity` (live), `cpu`, `layers`, `git-branch`, `server`, `network`, `gauge`, `settings`, `chevron-right` (flow), `copy`, `printer`, `download`.
- Do not use emoji as icons.

## 6. Charts (Chart.js)

Set once, before creating charts:

```js
Chart.defaults.font.family = 'Inter';
Chart.defaults.color = '#64748b';
Chart.defaults.borderColor = '#e2e8f0';
Chart.defaults.plugins.legend.position = 'bottom';
Chart.defaults.plugins.legend.labels.boxWidth = 14;
Chart.defaults.plugins.legend.labels.padding = 16;
Chart.defaults.plugins.legend.labels.color = '#1e293b';
Object.assign(Chart.defaults.plugins.tooltip, {
  backgroundColor: '#0f172a', titleColor: '#f8fafc', bodyColor: '#e2e8f0',
  borderColor: '#334155', borderWidth: 1, padding: 10,
});
```

- Container: `<div class="relative h-64"><canvas id="…"></canvas></div>`, options `responsive: true, maintainAspectRatio: false`.
- Bars: `borderRadius: 4`, `borderWidth: 1`, border = one shade darker than fill. Hide x grid (`grid: { display: false }`).
- Doughnut: `cutout: '66%'`, `borderColor: '#ffffff'`, `borderWidth: 2`, legend `right`.
- Line: `tension: 0.35`, `fill: true`, fill = stroke at 15% alpha, highlight anomalous points in rose.
- Axis ticks include units via `callback: v => v + ' ms'`.
- Thresholds/SLAs: show them in the card header chip *and* in the footer legend row.
- Dark theme: grid `rgba(51,65,85,0.4)`, ticks `#94a3b8`.

## 7. Dark theme ("control room")

Use only when the subject is ops/AI/telemetry/live system, or the user asks. Same layout and components; swap tokens via the Dark columns above. Add subtle glow blobs: `absolute w-[600px] h-[350px] bg-cyan-500/20 blur-[130px] rounded-full opacity-30 pointer-events-none`. Primary accent becomes `cyan` (`text-cyan-400`, buttons `bg-cyan-600 hover:bg-cyan-500`).

## 8. Motion

Only subtle and purposeful:
- `transition` on hover states; `hover:-translate-y-1` for clickable tiles; `active:scale-95` on buttons.
- `animate-pulse` / `animate-ping` on a *single* "live/current" dot.
- Drawer slides `transform translate-x-full transition-transform duration-300`.
- Animated dashed SVG flow lines (`stroke-dasharray: 6 6` + keyframed `stroke-dashoffset`) for data-flow diagrams.

Never: auto-playing carousels, bouncing elements, parallax.
