## ADP0 Sandbox Template

An opinionated starter template for building AI-driven product sandboxes with a premium, extensible design system. This project uses Vite + React + TypeScript + Tailwind CSS with a layer of semantic design tokens (CSS variables) to make automated styling by AI agents simple, safe, and powerful.

### Key Features

* Modern React + Vite + TypeScript setup
* Tailwind CSS with extended theme tokens (color system, spacing scale, typography, radius, shadows)
* Component library scaffold (buttons, forms, overlays, navigation, feedback, layout primitives)
* Dark mode ready via class strategy (`.dark`)
* AI-friendly theming: stable, semantic CSS variable contract

### Project Goals

1. Provide a clean sandbox for rapid iteration of AI-driven UI prototypes.
2. Expose a predictable design token surface so autonomous agents can safely adjust branding.
3. Maintain premium visual quality out-of-the-box (refined color ramps, spacing rhythm, typography scale).

---
## Getting Started

Install dependencies and run the dev server:

```powershell
npm install
npm run dev
```

Build for production:

```powershell
npm run build
```

Preview production build:

```powershell
npm run preview
```

---
## Design System Overview

The design system is driven by CSS variables defined in `src/index.css` (or a future `tokens.css`) and mapped into Tailwind via `tailwind.config.ts`.

### Token Layers

1. Primitive Tokens (e.g. `--color-base-50`, `--color-accent-500`)
2. Semantic Tokens (e.g. `--foreground`, `--bg-surface`, `--border-muted`)
3. Component Aliases (applied within component files when needed)

### Why CSS Variables?

* Runtime theming without rebuild
* AI agents can patch variables deterministically
* Supports user personalization (themes, accessibility modes)

### Color System Philosophy

The palette provides balanced neutral, accent, and utility scales with consistent contrast steps. Each ramp is roughly 8–10 steps: 50 → 950. Example categories:

* Neutral (gray / slate hybrid)
* Accent (brand primary: `accent`)
* Secondary accent (optional: `brand-alt`)
* Supporting: success, warning, danger, info

### Spacing & Sizing

We extend Tailwind spacing with a refined modular scale for macro layout + micro-refinement:

| Step | Token | px |
|------|-------|----|
| -2 | `space-1xs` | 2 |
| -1 | `space-xs` | 4 |
| 0 | `space-sm` | 8 |
| 1 | `space-md` | 12 |
| 2 | `space-lg` | 16 |
| 3 | `space-xl` | 20 |
| 4 | `space-2xl` | 24 |
| 5 | `space-3xl` | 32 |
| 6 | `space-4xl` | 40 |
| 7 | `space-5xl` | 56 |
| 8 | `space-6xl` | 72 |

Mapped in Tailwind via `spacing` and additional utilities (padding, gap, margin).

### Typography

Font stacks favor legibility + system fallback:

* Display: `var(--font-display, "Inter", system-ui, sans-serif)`
* Body: `var(--font-body, "Inter", system-ui, sans-serif)`
* Mono: `var(--font-mono, "JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, monospace)`

Scale (example): 12, 14, 16, 18, 20, 24, 30, 36, 48, 60.

### Radii & Elevation

* Radii tokens: `--radius-xs`, `--radius-sm`, `--radius-md`, `--radius-lg`, `--radius-full`.
* Shadows tuned for subtle layering: `--shadow-xs` .. `--shadow-xl`.

---
## AI Agent Customization Guide

Agents can safely modify theme by editing only the variable block in the root stylesheet. Avoid direct Tailwind config rewrites unless adding new semantic tokens.

### Contract for Agents

* Do not remove existing variable names; add new ones if needed.
* Keep contrast ratios ≥ 4.5:1 for body text vs background.
* Prefer adjusting primitives; semantic tokens map to primitives.

### Example: Adjust Accent Brand

Change just these lines (example values):
```css
:root {
	--color-accent-400: #5d8bff;
	--color-accent-500: #3d6dff;
	--color-accent-600: #2551d6;
}
```
Tailwind classes like `text-accent-600` or `bg-accent-500` update instantly.

### Programmatic Patch (Pseudo JSON Instruction)
```json
{
	"action": "update-theme",
	"tokens": {
		"--color-accent-500": "#3f51ff",
		"--color-accent-600": "#2f40cc"
	}
}
```

---
## Extending the System

1. Add new primitive colors: define `--color-newname-50..900`.
2. Map to Tailwind in `tailwind.config.ts` under `theme.extend.colors`.
3. (Optional) Introduce semantic alias: `--bg-highlight`, etc.
4. Use semantic variable inside components when meaning > hue.

---
## Folder Structure (Excerpt)

```
src/
	components/ui/*    # Reusable UI primitives
	pages/             # Route-level pages
	hooks/             # Custom React hooks
	lib/               # Utilities
	index.css          # Base styles + tokens
```

---
## Roadmap Ideas

* Theming presets (light / dark / high-contrast / dim)
* Dynamic theme generator endpoint
* Automated accessibility audit script
* Motion token layer (durations, easings)

---
## License

MIT. Attribution appreciated but not required.

---
## Contributing

PRs welcome. For significant changes, open an issue describing the goal first.

---
## Support

Questions or suggestions: open an issue.

---
Happy building with ADP0 Sandbox Template.
