# Infographics — Claude Code plugin

Lets Claude make single-file interactive HTML infographics in the Yunex Traffic house style: Tailwind, Inter + JetBrains Mono, slate neutrals, fixed semantic accent colors, Lucide icons and Chart.js. Every page can be read as a scrolling **article** or presented as **slides**.

## What's inside

```
.claude-plugin/
  marketplace.json      # marketplace "yunex-traffic" listing this plugin
  plugin.json           # plugin "infographics"
skills/infographic/
  SKILL.md              # workflow, archetypes, rules, checklist
  references/           # design-system.md (tokens), components.md (snippets)
  assets/template.html  # starting skeleton for every new page
```

## Installation

You need [Claude Code](https://docs.claude.com/en/docs/claude-code) with plugin support.

### 1. Add the marketplace

Run this inside Claude Code. Point it at a local clone:

```
/plugin marketplace add /path/to/infographics-skill
```

or at the hosted Git repository:

```
/plugin marketplace add <org>/<repo>              # GitHub shorthand
/plugin marketplace add https://<host>/<repo>.git # any Git URL
```

### 2. Install the plugin

```
/plugin install infographics@yunex-traffic
```

You can also run `/plugin` with no arguments and pick **infographics** from the menu. Restart Claude Code if it asks you to.

### 3. Check that it worked

Run `/plugin` and confirm that **infographics** is listed as enabled. The skill shows up as `infographics:infographic`.

### Updating and removing

```
/plugin marketplace update yunex-traffic   # pull the latest version
/plugin uninstall infographics@yunex-traffic
```

### Team-wide setup (optional)

To have the plugin offered automatically to everyone working in a repository, add this to that repository's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "yunex-traffic": {
      "source": { "source": "git", "url": "https://<host>/<repo>.git" }
    }
  },
  "enabledPlugins": {
    "infographics@yunex-traffic": true
  }
}
```

### Local development

To try changes to the skill without installing it, start Claude Code with the plugin directory loaded:

```
claude --plugin-dir /path/to/infographics-skill
```

## Usage

The skill starts on its own when you ask for an infographic, one-pager, visual summary, report page, process/timeline/architecture/org diagram, or HTML slide deck. You can also call it directly:

```
/infographics:infographic <what you want>
```

### Example prompts

```
Make an infographic from test-results.csv comparing latency of camera A vs B.
Show p50/p95/p99 and say which one passes the 120 ms SLA.
```

```
Turn docs/release-process.md into a tabbed process explainer
with a stepper for the release phases.
```

```
Create a timeline infographic of the HW 2.0 milestones below. Present it as slides.
<paste milestones>
```

```
Explain our hostname naming scheme as an anatomy/spec page with a decoder
where I can paste a hostname and see each segment explained.
```

### What you get

- One self-contained `<topic>_infographic.html` file in your target folder. Open it in any browser; it needs an internet connection for the CDN fonts and libraries.
- An **Article / Slides** switch in the header. In slides mode, the bottom bar lists the slide titles so you can jump to any slide; when there are too many to fit, the `^` button opens the full list. The zoom controls next to prev/next scale only the slide content (keys `-`, `0` for 100%, `+`, and `W` for fit to width). You can also use `←` / `→`, PageUp/PageDown, Home/End or swipe; `#slide-3` in the URL opens slide 3. Printing in slides mode gives one slide per page.
- A layout chosen to fit your content:

| Archetype | Good for | Example |
|---|---|---|
| Report / Benchmark | measurements, A-vs-B, SLA results | [camera_latency_performance_report_infographic.html](examples/camera_latency_performance_report_infographic.html) |
| Anatomy / Spec | formats, naming schemes, standards | [hostname_and_serial_number_infographic.html](examples/hostname_and_serial_number_infographic.html) |
| Process Explainer (tabbed) | release processes, SDLC, playbooks | [awareai_release_process_infographic.html](examples/awareai_release_process_infographic.html), [ai_native_sdlc_infographics.html](examples/ai_native_sdlc_infographics.html) |
| Diagram / Timeline | roadmaps, org structures, architectures | [awareai_hw_2_0_timeline_infographic.html](examples/awareai_hw_2_0_timeline_infographic.html), [ai_native_sdlc_org_structure.html](examples/ai_native_sdlc_org_structure.html) |
| Ops Blueprint (dark) | AI copilots, telemetry, live systems | [dmp_ai_operations_lifecycle_copilot_infographic.html](examples/dmp_ai_operations_lifecycle_copilot_infographic.html) |

### Tips for good results

- **Give it the real data.** The skill never invents numbers, names or quotes. If something is missing it will ask you or leave the slot out.
- **Say whether numbers are measured or estimated.** Values are labeled `Measured`, `Estimated`, `Derived` or `Quoted`.
- **Name the audience and the key message**, e.g. "for management: B is ready to ship".
- **Ask for slides** ("present it as slides", "split X and Y onto separate slides") when you need a deck. Claude follows any split you specify.
- **Iterate in plain language**: "make the chart a bar chart", "switch to the dark theme", "add a table of raw results".
