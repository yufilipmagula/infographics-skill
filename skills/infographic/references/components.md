# Component Library

Copy these snippets and change only content and the accent color (`{c}` = an accent from design-system.md). Light theme shown; for dark, swap tokens per design-system.md §3.

## Contents
1. Header · 2. Hero banner · 3. KPI card · 4. Section card · 5. Feature card · 6. Stat strip · 7. Step / pipeline card · 8. Category card (top accent) · 9. Data table · 10. Badges & chips · 11. Lists · 12. Callouts · 13. Dark output panel · 14. Comparison gradient card · 14b. Chart threshold lines · 15. Formula block · 16. Footer
Interactive: 17. Tabs · 18. Stepper + detail · 19. Inspector drawer · 20. Modal · 21. Toast + copy · 22. Toggle switch · 23. Simulator / qualifier · 24. Filter pills

---

## 1. Header (sticky, always present)

```html
<header class="sticky top-0 z-50 border-b border-slate-200 bg-white/90 backdrop-blur shadow-sm">
  <div class="px-5 py-4 flex flex-col md:flex-row md:items-center md:justify-between gap-4">
    <div class="flex items-center gap-3">
      <svg class="h-11 w-auto shrink-0" viewBox="-6.415 0 51.584 56.005" role="img" aria-label="Yunex Traffic"><defs><linearGradient id="brand-mark-gradient" x1="0.904" x2="-0.737" y1="1.287" y2="-0.774" gradientUnits="objectBoundingBox"><stop offset="0" stop-color="#affad7"/><stop offset="0.44" stop-color="#9dbbff"/><stop offset="1" stop-color="#1e2ed9"/></linearGradient><clipPath id="brand-mark-clip"><path d="M3.585 0H45.169V56.005H3.585A10 10 0 0 1-6.415 46.005V10A10 10 0 0 1 3.585 0Z"/></clipPath></defs><g clip-path="url(#brand-mark-clip)"><path fill="url(#brand-mark-gradient)" d="M-4648.054-117.8h-6.686l14.511-19.737 26.36-36.26h6.329l-20.391 28.186 20.4 27.812h-6.031l-16.856-22.928-3.117 4.289 13.7 18.637-28.208-.013-.014.019Zm-11.061-2.578v-50.858l18.7 25.429-18.7 25.427Zm21.832-29.693-17.449-23.728h6.125l.017.021 28.75-.015-17.441 23.722Z" transform="translate(4652.7 173.8)"/></g></svg>
      <div>
        <div class="flex items-center gap-2">
          <span class="text-[10px] uppercase font-extrabold tracking-widest text-sky-700 bg-sky-50 px-2 py-0.5 rounded border border-sky-200">Team or product</span>
          <span class="text-xs text-slate-500 font-mono">v1.0 • Category</span>
        </div>
        <h1 class="text-lg sm:text-xl font-extrabold tracking-tight text-slate-900 mt-0.5">Title of the Infographic</h1>
      </div>
    </div>
    <div class="flex items-center gap-3 no-print">
      <!-- optional: key constraint, tabs (17); always: Article/Slides toggle (copy from template), print button -->
      <div class="text-right hidden sm:block">
        <div class="text-xs font-medium text-slate-500">Key Constraint</div>
        <div class="text-sm font-mono font-bold text-amber-600">1,000 ms</div>
      </div>
      <button onclick="window.print()" class="px-3.5 py-2 text-xs font-semibold rounded-lg bg-white hover:bg-slate-50 text-slate-700 border border-slate-300 shadow-sm flex items-center gap-1.5 transition active:scale-95">
        <i data-lucide="printer" class="w-4 h-4 text-slate-500"></i> Export / Print
      </button>
    </div>
  </div>
</header>
```

## 2. Hero banner

```html
<section class="relative rounded-2xl border border-slate-200 bg-gradient-to-r from-white via-slate-50 to-white p-6 lg:p-8 overflow-hidden shadow-sm">
  <div class="absolute top-0 right-0 h-64 w-64 bg-emerald-500/5 blur-3xl rounded-full -mr-20 -mt-20 pointer-events-none"></div>
  <div class="absolute bottom-0 left-1/3 h-48 w-48 bg-sky-500/5 blur-3xl rounded-full pointer-events-none"></div>
  <div class="relative max-w-3xl space-y-4">
    <h2 class="text-2xl md:text-3xl font-extrabold text-slate-900 leading-tight">
      Plain statement of the topic:<br>
      <span class="bg-gradient-to-r from-sky-600 to-emerald-600 bg-clip-text text-transparent">The key message in one line</span>
    </h2>
    <p class="text-sm md:text-base text-slate-600 leading-relaxed">Two-to-three sentence summary.</p>
    <div class="flex flex-wrap gap-3 pt-1 text-xs font-mono text-slate-600">
      <span class="flex items-center gap-1.5 bg-white px-3 py-1.5 rounded-full border border-slate-200 shadow-sm">
        <i data-lucide="shield" class="w-3.5 h-3.5 text-sky-600"></i> Highlight chip
      </span>
    </div>
  </div>
</section>
```

Centered variant (spec/anatomy pages): `<div class="text-center max-w-3xl mx-auto space-y-3">` + h2 `text-3xl sm:text-4xl font-extrabold tracking-tight` + p.

## 3. KPI card (headline number)

```html
<div class="bg-white border border-slate-200 rounded-2xl p-6 shadow-sm hover:shadow-md transition">
  <div class="flex items-center justify-between">
    <span class="text-xs font-semibold uppercase tracking-wider text-slate-500">Metric Name</span>
    <span class="text-xs font-semibold text-emerald-700 bg-emerald-50 px-2 py-0.5 rounded border border-emerald-200">Measured</span>
  </div>
  <div class="mt-3 flex items-baseline gap-2">
    <span class="text-4xl font-extrabold font-mono tracking-tight text-emerald-600">790 ms</span>
    <span class="text-xs font-mono font-medium text-slate-500">Total chain delay</span>
  </div>
  <p class="mt-3 text-xs leading-relaxed text-slate-600">One sentence interpreting the number, with <strong class="text-slate-900">the key fact</strong>.</p>
  <div class="mt-4 pt-3 border-t border-slate-100 flex items-center gap-1.5 text-xs font-semibold text-emerald-700">
    <i data-lucide="check-circle-2" class="w-4 h-4 shrink-0"></i> Consequence / margin
  </div>
</div>
```

Use in pairs (`grid md:grid-cols-2 gap-5`) for A-vs-B, or 3–4 for dashboards. Badge + number + footer share the semantic accent.

## 4. Section card (container for charts, flows, content)

```html
<section class="bg-white border border-slate-200 rounded-2xl p-6 shadow-sm">
  <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 mb-6">
    <div>
      <h3 class="text-base font-bold text-slate-900">Section Title</h3>
      <p class="text-xs text-slate-500 mt-0.5">What this section shows</p>
    </div>
    <span class="text-xs font-mono px-2.5 py-1 rounded bg-slate-100 text-slate-700 border border-slate-200 font-medium">Unit / Scope</span>
  </div>
  <!-- content: <div class="relative h-64"><canvas id="c1"></canvas></div> -->
  <div class="mt-4 pt-4 border-t border-slate-100 grid grid-cols-2 text-xs text-slate-600">
    <div class="flex items-center"><span class="w-2.5 h-2.5 rounded-full bg-emerald-500 mr-2"></span>A: <strong class="ml-1 text-slate-800">takeaway</strong></div>
    <div class="flex items-center"><span class="w-2.5 h-2.5 rounded-full bg-rose-500 mr-2"></span>B: <strong class="ml-1 text-rose-600">takeaway</strong></div>
  </div>
</section>
```

## 5. Feature / objective card

```html
<div class="bg-white p-5 rounded-xl border border-slate-200 shadow-sm hover:shadow-md transition">
  <div class="h-10 w-10 rounded-lg bg-{c}-50 border border-{c}-100 flex items-center justify-center mb-4">
    <i data-lucide="zap" class="h-5 w-5 text-{c}-600"></i>
  </div>
  <h3 class="font-bold text-slate-900 text-sm mb-1">Objective</h3>
  <p class="text-xs text-slate-500 leading-relaxed">One or two sentences.</p>
</div>
```

Grid: `grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4`, one accent per card from the categorical order.

## 6. Stat strip (small numbers inside a card)

```html
<div class="grid grid-cols-1 md:grid-cols-3 gap-4 font-mono text-center">
  <div class="bg-slate-50 p-4 rounded-lg border border-slate-200/80 shadow-inner">
    <span class="block text-2xl font-black text-slate-900">2</span>
    <span class="block text-[10px] text-slate-500 uppercase tracking-widest mt-1">Releases / Yr</span>
  </div>
</div>
```

## 7. Step / pipeline card

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-6 gap-3">
  <div class="bg-slate-50/70 border border-slate-200 rounded-xl p-4 flex flex-col justify-between hover:border-slate-300 transition">
    <div>
      <div class="flex items-center justify-between">
        <span class="text-[10px] font-mono font-bold uppercase tracking-wider text-slate-400">Step 01</span>
        <span class="text-[10px] font-mono font-semibold text-slate-500 bg-white border border-slate-200 px-1.5 py-0.5 rounded">T₀ = 0 ms</span>
      </div>
      <div class="font-bold text-sm text-slate-900 mt-2 flex items-center gap-1.5">
        <i data-lucide="monitor" class="w-4 h-4 text-slate-500"></i> Stage name
      </div>
      <p class="text-xs text-slate-600 mt-2 leading-relaxed">What happens here.</p>
    </div>
    <div class="mt-4 pt-3 border-t border-slate-200/60 text-[11px] font-mono font-semibold text-slate-700">
      430 ms <span class="text-slate-400 font-normal">(qualifier)</span>
    </div>
  </div>

  <!-- Highlighted step: thicker accent border + floating pill -->
  <div class="relative bg-slate-50/70 border-2 border-sky-200 rounded-xl p-4 flex flex-col justify-between">
    <div class="absolute -top-2.5 right-3 bg-sky-600 text-white text-[9px] font-mono font-bold px-2 py-0.5 rounded-full uppercase">Bottleneck</div>
    …
  </div>
</div>
```

Simple linear flow with arrows: alternate step boxes with `<div class="hidden md:flex items-center justify-center text-slate-400"><i data-lucide="chevron-right"></i></div>` in a grid whose arrow columns are auto-width, e.g. 4 steps: `grid grid-cols-1 md:grid-cols-[1fr_auto_1fr_auto_1fr_auto_1fr] gap-3`.

## 8. Category card (top accent)

```html
<div class="bg-white rounded-xl border border-slate-200 border-t-4 border-t-{c}-500 shadow-sm hover:shadow-md transition p-6 flex flex-col justify-between space-y-6">
  <div class="space-y-4">
    <div class="flex justify-between items-center">
      <span class="text-[10px] uppercase font-extrabold tracking-wider text-{c}-700 bg-{c}-50 border border-{c}-200 px-2.5 py-1 rounded">Label</span>
      <span class="text-xs text-slate-400 font-mono">2× per year</span>
    </div>
    <h3 class="text-xl font-bold text-slate-900">Category Name</h3>
    <p class="text-sm text-slate-600 leading-relaxed">Description.</p>
    <div class="border-t border-slate-100 pt-4 space-y-2 text-xs">
      <span class="block font-semibold uppercase tracking-wider text-slate-700">Scope:</span>
      <ul class="space-y-1.5 text-slate-500 list-disc list-inside"><li>Item</li></ul>
    </div>
  </div>
  <div class="bg-slate-50 p-3 rounded-lg border border-slate-200/80 text-xs font-mono text-center text-{c}-700 shadow-inner">Target: …</div>
</div>
```

Tinted variant (segment explanation): `bg-{c}-50/60 rounded-2xl p-5 border border-{c}-200/80` with a `w-8 h-8 rounded-lg bg-{c}-500 text-white` number tile "01" top-left and the icon top-right.

## 9. Data table

```html
<section class="bg-white border border-slate-200 rounded-2xl overflow-hidden shadow-sm">
  <div class="p-6 border-b border-slate-200 bg-slate-50/50 flex flex-col sm:flex-row justify-between sm:items-center gap-2">
    <div>
      <h3 class="text-base font-bold text-slate-900">Table Title</h3>
      <p class="text-xs text-slate-500">What is compared</p>
    </div>
    <span class="text-xs font-mono font-semibold bg-sky-50 text-sky-700 border border-sky-200 px-3 py-1 rounded-full">Limit: 1,000 ms</span>
  </div>
  <div class="overflow-x-auto">
    <table class="w-full text-left text-xs sm:text-sm">
      <thead class="bg-slate-100/70 text-slate-600 font-mono text-xs uppercase tracking-wider border-b border-slate-200">
        <tr><th class="py-3.5 px-4 sm:px-6">Component</th><th class="py-3.5 px-4">A</th><th class="py-3.5 px-4">B</th><th class="py-3.5 px-4">Δ</th></tr>
      </thead>
      <tbody class="divide-y divide-slate-100 font-mono">
        <tr class="hover:bg-slate-50/80 transition">
          <td class="py-3.5 px-4 sm:px-6 font-sans font-medium text-slate-900">Row name
            <span class="block text-xs font-normal text-slate-500">Row explanation</span></td>
          <td class="py-3.5 px-4 font-bold text-emerald-700">100 ms</td>
          <td class="py-3.5 px-4 font-bold text-rose-600">750 ms</td>
          <td class="py-3.5 px-4 font-semibold text-rose-600">+650 ms</td>
        </tr>
        <!-- subtotal -->
        <tr class="bg-sky-50/50 border-t-2 border-slate-200 font-semibold text-sky-900">…</tr>
        <!-- total -->
        <tr class="bg-slate-100 text-base font-bold">…</tr>
      </tbody>
    </table>
  </div>
  <div class="px-6 py-3 bg-slate-50 text-[11px] text-slate-500 border-t border-slate-200">* Footnote explaining assumptions / sources.</div>
</section>
```

Unchanged values: `text-slate-400` ("0 ms (ident.)").

## 10. Badges & chips

| Kind | Markup |
|---|---|
| Status badge | `<span class="text-xs font-semibold text-{c}-700 bg-{c}-50 px-2 py-0.5 rounded border border-{c}-200">Measured</span>` |
| Pill with dot | `<span class="inline-flex items-center gap-1.5 px-2.5 py-0.5 rounded-full text-xs font-semibold bg-{c}-50 text-{c}-700 border border-{c}-200"><span class="w-1.5 h-1.5 rounded-full bg-{c}-500"></span>Label</span>` |
| Live pill | dot gets `animate-ping` wrapper: `<span class="relative flex h-2.5 w-2.5"><span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span><span class="relative inline-flex rounded-full h-2.5 w-2.5 bg-emerald-500"></span></span>` |
| Mono unit chip | `<span class="text-xs font-mono font-medium px-2.5 py-1 rounded bg-slate-100 text-slate-700 border border-slate-200">ms</span>` |
| Tag | `<span class="px-2 py-0.5 rounded-md bg-slate-100 text-slate-700 text-[11px] font-mono border border-slate-200">#tag</span>` |
| Inline code | `<code class="font-mono text-[0.9em] bg-slate-100 px-1 py-0.5 rounded text-slate-800">config.yaml</code>` |
| Legend item | `<span class="flex items-center gap-1.5 text-xs text-slate-700 font-medium"><span class="w-3 h-3 rounded bg-{c}-100 border border-{c}-500"></span>Label</span>` |

## 11. Lists

```html
<ul class="space-y-2 text-xs text-slate-600">
  <li class="flex items-start gap-2"><i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-500 shrink-0 mt-0.5"></i><span><strong class="text-slate-800">Lead:</strong> detail.</span></li>
  <li class="flex items-start gap-2 text-slate-400"><i data-lucide="minus" class="w-4 h-4 shrink-0 mt-0.5"></i><span>Optional / not applicable.</span></li>
  <li class="flex items-start gap-2"><i data-lucide="x-circle" class="w-4 h-4 text-rose-500 shrink-0 mt-0.5"></i><span>Failure reason.</span></li>
</ul>
```

Numbered waves/phases: `<div class="flex gap-4 items-start bg-slate-50 p-4 rounded-lg border border-slate-200/80">` + `h-6 w-6 rounded bg-{c}-50 border border-{c}-200 text-{c}-700 text-xs font-bold font-mono` tile ("W1") + title `text-xs uppercase font-extrabold text-slate-800` + `text-xs text-slate-500` body.

## 12. Callouts

```html
<!-- Rule / constraint ribbon -->
<div class="flex items-center gap-4 p-4 rounded-2xl bg-slate-50 border border-slate-200">
  <div class="w-12 h-12 rounded-xl bg-{c}-100 text-{c}-700 flex items-center justify-center shrink-0"><i data-lucide="gauge" class="w-6 h-6"></i></div>
  <div>
    <div class="text-xs font-bold uppercase text-slate-400">Constraint</div>
    <div class="text-sm font-bold text-slate-800">The rule in one line</div>
    <p class="text-xs text-slate-500 mt-0.5">Short explanation.</p>
  </div>
</div>

<!-- Side note ("How X differs") -->
<div class="bg-slate-50 p-5 rounded-lg border border-slate-200">
  <div class="flex items-center gap-2 text-amber-800 font-extrabold text-xs uppercase tracking-wider"><i data-lucide="alert-circle" class="h-4 w-4 text-amber-600"></i>How exceptions differ</div>
  <p class="text-xs text-slate-600 leading-relaxed mt-3">…</p>
</div>

<!-- Insight box -->
<div class="p-4 rounded-xl border border-sky-200 bg-sky-50/70 space-y-2">
  <h4 class="text-xs font-bold text-sky-900 flex items-center gap-1.5"><i data-lucide="zap" class="w-4 h-4 text-sky-600"></i>Key insights</h4>
  <ul class="text-[11px] text-slate-700 space-y-1.5 list-disc list-inside"><li><strong>Lead:</strong> point.</li></ul>
</div>
```

## 13. Dark output panel (computed values, terminal)

```html
<div class="bg-slate-900 text-white p-6 sm:p-8 rounded-2xl shadow-inner">
  <span class="text-xs font-bold text-sky-400 uppercase tracking-widest">Real-time Computed Output</span>
  <div class="mt-4 text-xs text-slate-400 flex items-center gap-1.5"><i data-lucide="terminal" class="w-3.5 h-3.5"></i>Label</div>
  <div class="mt-1 text-2xl sm:text-4xl font-mono font-bold tracking-wider text-sky-400 bg-slate-800/80 px-4 py-3 rounded-xl border border-slate-700">AP0301001</div>
  <div class="mt-6 pt-4 border-t border-slate-800 grid grid-cols-3 gap-2 text-center text-xs">
    <div class="bg-slate-800/60 p-2 rounded-lg"><div class="text-[10px] uppercase text-slate-400">Field</div><div class="font-mono font-bold text-emerald-400 mt-0.5">Value</div></div>
  </div>
</div>
```

Terminal header: three dots `w-3 h-3 rounded-full bg-rose-500/80 | bg-amber-500/80 | bg-emerald-500/80` + `text-xs font-mono text-slate-400` session name.

## 14. Comparison gradient card (two identities side by side)

```html
<div class="relative overflow-hidden rounded-3xl p-6 sm:p-8 text-white bg-gradient-to-b from-sky-500 to-blue-600 shadow-xl shadow-sky-500/20 flex flex-col justify-between">
  <div class="absolute -right-10 -bottom-10 opacity-10"><i data-lucide="network" class="w-56 h-56"></i></div>
  <div>
    <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/20 text-xs font-semibold mb-4"><i data-lucide="network" class="w-3.5 h-3.5"></i>Kind</div>
    <h3 class="text-xl sm:text-2xl font-black tracking-tight">Name</h3>
    <p class="text-sky-100 text-sm mt-1">Purpose.</p>
    <div class="mt-6 bg-black/25 rounded-2xl p-4 border border-white/20">
      <span class="text-[10px] uppercase font-bold text-sky-200 tracking-wider">Example</span>
      <div class="text-2xl sm:text-3xl font-mono font-bold tracking-wider mt-1">VALUE</div>
    </div>
  </div>
  <div class="mt-6 pt-4 border-t border-white/20 text-xs text-sky-100 flex items-center gap-2"><i data-lucide="alert-circle" class="w-4 h-4 shrink-0"></i><span><strong>Rule:</strong> …</span></div>
</div>
```

Second card: `from-emerald-600 to-teal-700`, `text-emerald-100/200`.

## 14b. Threshold / reference lines in Chart.js (no plugin library)

```js
const thresholdLines = {
  id: 'thresholdLines',
  afterDatasetsDraw(chart, _args, opts) {
    const { ctx, chartArea: { left, right }, scales: { y } } = chart;
    (opts.lines || []).forEach(({ value, label, color = '#f59e0b', dash = [6, 4] }) => {
      const py = y.getPixelForValue(value);
      ctx.save();
      ctx.strokeStyle = color; ctx.lineWidth = 1.5; ctx.setLineDash(dash);
      ctx.beginPath(); ctx.moveTo(left, py); ctx.lineTo(right, py); ctx.stroke();
      ctx.setLineDash([]); ctx.fillStyle = color; ctx.font = '600 10px "JetBrains Mono", monospace';
      ctx.textAlign = 'right'; ctx.fillText(label, right - 4, py - 4);
      ctx.restore();
    });
  },
};
// usage: plugins: [thresholdLines], options: { plugins: { thresholdLines: { lines: [{ value: 90, label: 'Throttle 90 °C' }] } } }
```

Threshold = amber dashed; baseline/ambient = slate-400 (`#94a3b8`) dashed. Mirror each line in the card's footer legend.

## 15. Formula / code block

```html
<div class="bg-slate-50 p-3.5 rounded-xl border border-slate-200 font-mono text-xs text-slate-800 overflow-x-auto">
  T_total = T_camera (750 ms) + T_analytics (430 ms) + … ≈ 1,440 ms
</div>
```

Formal summary sections: `<article class="bg-white border border-slate-200 rounded-2xl p-6 sm:p-8 space-y-6 shadow-sm">` with numbered `h4 class="text-base font-bold text-slate-900"` ("1. Objective") and `text-sm leading-relaxed text-slate-700` paragraphs.

## 16. Footer

```html
<footer class="mt-16 border-t border-slate-200 bg-white py-6 text-xs text-slate-500">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-2">
    <p>© 2026 Yunex Traffic</p>
    <div class="flex items-center gap-4 text-slate-400">
      <span>Source: <strong class="text-slate-700">…</strong></span><span>•</span><span>Report date <span class="font-mono">2026-10-19</span></span>
    </div>
  </div>
</footer>
```

---

# Interactive patterns

Rules: vanilla JS in one `<script>` at the end of `<body>`; data in a `const` array/object at the top of that script; render functions build DOM from data; re-run `lucide.createIcons()` after each render. Interactive elements are `<button>`s (keyboard accessible). `Escape` closes drawers/modals.

## 17. Tabs (segmented control)

```html
<nav class="article-only flex flex-wrap gap-1 bg-slate-100 p-1 rounded-xl border border-slate-200">
  <button data-tab="overview" class="tab-btn px-3 py-1.5 rounded-lg text-xs transition-all">Overview</button>
  <button data-tab="process" class="tab-btn px-3 py-1.5 rounded-lg text-xs transition-all">Process</button>
</nav>
…
<div data-panel="overview" class="space-y-8">
  <section data-slide="Overview">…</section>
  <section data-slide="Key figures">…</section>
</div>
<div data-panel="process" class="space-y-8 hidden">
  <section data-slide="Process steps">…</section>
</div>
```

```js
const TAB_ON = 'bg-white text-slate-900 font-semibold shadow-sm border border-slate-200/50';
const TAB_OFF = 'text-slate-600 font-medium hover:text-slate-900 hover:bg-slate-200/50';
function switchTab(id) {
  document.querySelectorAll('[data-panel]').forEach(p => p.classList.toggle('hidden', p.dataset.panel !== id));
  document.querySelectorAll('.tab-btn').forEach(b => {
    const on = b.dataset.tab === id;
    TAB_ON.split(' ').forEach(c => b.classList.toggle(c, on));
    TAB_OFF.split(' ').forEach(c => b.classList.toggle(c, !on));
  });
}
document.querySelectorAll('.tab-btn').forEach(b => b.addEventListener('click', () => switchTab(b.dataset.tab)));
switchTab('overview');
```

Each tab panel opens with a centered heading: `<div class="text-center max-w-xl mx-auto space-y-2"><h2 class="text-2xl font-extrabold text-slate-900">…</h2><p class="text-sm text-slate-500">…</p></div>` — put it inside the panel's first slide, since non-slide content is hidden in slides mode. Tab nav is `article-only`: in slides mode the slide panel replaces it, grouped by tab.

## 18. Stepper + detail panel

Buttons grid `grid grid-cols-2 sm:grid-cols-3 md:grid-cols-{N} gap-2`, each button shows mono number + short title. Active: `bg-{c}-600 border-{c}-600 text-white shadow-md`; inactive: `bg-white border-slate-200 text-slate-800 hover:border-slate-300` with number in `text-{c}-600`. Below: a section card with badge "Phase 01", h3 title, meta chips (`Responsible:`, `Stage:`), a 2/3 column for description + deliverables checklist and a 1/3 side note (callout 12).

```js
const STEPS = [{ num: '01', title: 'Scope & Approval', role: 'PO', stage: 'Initial', desc: '…', actions: ['…'], note: '…' }];
function selectStep(i) {
  const s = STEPS[i];
  el('step-title').textContent = s.title;           // use textContent for data
  el('step-actions').innerHTML = s.actions.map(a => `<li class="flex items-start gap-2.5">
    <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-500 shrink-0 mt-0.5"></i><span>${escapeHtml(a)}</span></li>`).join('');
  // toggle active classes on step buttons …
  lucide.createIcons();
}
```

## 19. Inspector drawer (details on click)

```html
<aside id="drawer" class="fixed top-0 right-0 bottom-0 w-full sm:w-[420px] bg-white border-l border-slate-200 p-6 z-50 shadow-2xl flex flex-col transform translate-x-full transition-transform duration-300 ease-out">
  <div class="flex items-center justify-between pb-4 border-b border-slate-200">
    <span id="drawer-badge" class="text-[11px] font-mono font-bold uppercase tracking-wider px-2.5 py-0.5 rounded bg-sky-50 text-sky-700 border border-sky-200">Phase 1</span>
    <button onclick="closeDrawer()" class="p-1.5 rounded-lg text-slate-400 hover:text-slate-700 hover:bg-slate-100"><i data-lucide="x" class="w-5 h-5"></i></button>
  </div>
  <div class="flex-1 overflow-y-auto py-5 space-y-5"><!-- date (mono, accent), h2 title, context box, tags, deliverables --></div>
  <div class="pt-4 border-t border-slate-200 flex justify-between text-xs font-mono text-slate-500">
    <button onclick="step(-1)">&larr; Previous</button><span id="drawer-count">1 of 17</span><button onclick="step(1)">Next &rarr;</button>
  </div>
</aside>
```

Open: `drawer.classList.remove('translate-x-full')`; close: add it back.

## 20. Modal

```html
<div id="modal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-900/40 backdrop-blur-sm">
  <div class="bg-white border border-slate-200 rounded-2xl max-w-lg w-full p-6 space-y-4 shadow-2xl">
    <div class="flex items-center justify-between"><h3 class="text-lg font-bold text-slate-900">Title</h3><button onclick="closeModal()" class="text-slate-400 hover:text-slate-700"><i data-lucide="x" class="w-5 h-5"></i></button></div>
    <div class="text-xs text-slate-600 space-y-3 leading-relaxed">…</div>
    <div class="flex justify-end"><button onclick="closeModal()" class="px-4 py-2 rounded-lg bg-sky-600 hover:bg-sky-700 text-white text-xs font-semibold shadow-sm">Got it</button></div>
  </div>
</div>
```

Show with `modal.classList.replace('hidden','flex')`.

## 21. Toast + copy to clipboard

```html
<div id="toast" class="fixed bottom-6 right-6 z-50 bg-slate-900 text-white px-5 py-3 rounded-2xl shadow-2xl border border-slate-700 flex items-center gap-3 translate-y-20 opacity-0 transition-all duration-300">
  <i data-lucide="check-circle-2" class="w-5 h-5 text-emerald-400"></i><span id="toast-msg" class="text-sm font-semibold"></span>
</div>
```

```js
let toastT;
function toast(msg) {
  const t = el('toast'); el('toast-msg').textContent = msg;
  t.classList.remove('translate-y-20', 'opacity-0');
  clearTimeout(toastT); toastT = setTimeout(() => t.classList.add('translate-y-20', 'opacity-0'), 2500);
}
async function copy(text) {
  try { await navigator.clipboard.writeText(text); }
  catch { const ta = Object.assign(document.createElement('textarea'), { value: text }); document.body.append(ta); ta.select(); document.execCommand('copy'); ta.remove(); }
  toast(`Copied ${text}`);
}
```

## 22. Toggle switch

```html
<div class="flex items-center justify-between p-3 rounded-lg bg-slate-50 border border-slate-200">
  <div><span class="block text-xs font-bold text-slate-800">Gate name</span><span class="text-[10px] text-slate-400">Explanation</span></div>
  <button role="switch" aria-checked="true" data-gate="regressions" class="gate h-6 w-12 rounded-full p-1 flex items-center justify-end bg-emerald-600 transition-all">
    <span class="h-4 w-4 rounded-full bg-white shadow-sm"></span>
  </button>
</div>
```

Off state: `bg-slate-300 justify-start`.

## 23. Simulator / qualifier

Left (`lg:col-span-2`) = controls (option buttons, toggles 22, inputs `w-full bg-white text-sm font-semibold px-3 py-2 rounded-xl border border-slate-300 focus:ring-2 focus:ring-sky-500 focus:outline-none`). Right = result card whose state box switches between:

| State | Box | Icon |
|---|---|---|
| pass | `bg-emerald-50 border-emerald-200`, title `text-emerald-800` | `check-circle-2` |
| warn | `bg-amber-50 border-amber-200`, title `text-amber-800` | `alert-triangle` |
| fail | `bg-rose-50 border-rose-200`, title `text-rose-800` | `alert-circle` |

followed by a list of reasons (`x-circle` rose items). Recompute on every input change; logic lives in one `evaluate(state) → { status, reasons }` function.

## 24. Filter pills

```html
<div class="inline-flex flex-wrap gap-1 p-1.5 bg-white border border-slate-200 rounded-2xl shadow-sm">
  <button data-filter="all" class="filter-btn px-3 py-1.5 text-xs rounded-xl font-medium bg-sky-600 text-white shadow-sm">All</button>
  <button data-filter="p1" class="filter-btn px-3 py-1.5 text-xs rounded-xl font-medium text-slate-600 hover:bg-slate-100 hover:text-slate-900">1. Phase</button>
</div>
```

Filtered-out items get `opacity-25` (not removed) so the layout stays stable.
