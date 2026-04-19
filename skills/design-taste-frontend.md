---
name: design-taste-frontend
description: "When the user wants a high-agency frontend build with explicit control over design variance, motion intensity, and visual density. Use when the user wants to tune how creative vs. structured, how animated vs. static, or how dense vs. airy their UI should be — or when they want premium React/Next.js components that avoid generic AI defaults."
category: design
tags: [frontend, React, Next.js, Tailwind, motion, design-system, high-agency, Framer-Motion]
version: 2.0.0
author: DivadSanders
---

# Design Taste Frontend

> High-agency frontend with tunable dials. Set the variance, motion, and density you want — Claude adapts every decision to match.

## What This Does

Gives Claude a senior frontend engineer's instincts, plus a configurable dial system that lets you control the feel of the output without having to explain it in words. Set three numbers. Claude does the rest.

## When to Use

- You want precise control over how creative vs. structured your UI should be
- You need premium React/Next.js components that don't look like they came from a template
- You want performance-correct, architecturally-sound code alongside the visuals
- You need to specify motion intensity or data density without writing a paragraph about it

## Example Prompts

- "Build a SaaS dashboard hero. DESIGN_VARIANCE: 7, MOTION_INTENSITY: 5, VISUAL_DENSITY: 6"
- "Create a bento grid feature section, max variance and motion, low density"
- "Build a login form with high-agency design taste — clean, modern, no emojis"

---

## The Dial System

Three global variables control how Claude generates the UI. Set them in your prompt or accept the defaults.

```
DESIGN_VARIANCE: 8    (1 = Perfect symmetry / 10 = Artsy asymmetry)
MOTION_INTENSITY: 6   (1 = Static / 10 = Cinematic physics)
VISUAL_DENSITY: 4     (1 = Art gallery / 10 = Pilot cockpit)
```

**Override in your prompt:** "Set DESIGN_VARIANCE to 5, keep everything else default"  
**Claude adapts automatically** — all architecture, typography, animation, and layout decisions flow from these values.

### DESIGN_VARIANCE Scale

| Level | Behavior |
|-------|----------|
| 1–3 | Flexbox `justify-center`, strict 12-column grids, equal paddings. Safe and predictable. |
| 4–7 | Overlapping margins (`margin-top: -2rem`), varied image ratios (4:3 next to 16:9), left-aligned headers over centered data. |
| 8–10 | Masonry layouts, fractional CSS Grid (`2fr 1fr 1fr`), massive empty zones (`padding-left: 20vw`). Asymmetric by design. |

**Rule at variance > 4:** Centered hero H1s are banned. Force Split Screen, Left/Right aligned, or Asymmetric Whitespace.

### MOTION_INTENSITY Scale

| Level | Behavior |
|-------|----------|
| 1–2 | No transitions. Static, zero-animation. |
| 3–5 | Subtle hover states. Opacity/translate entry animations. No physics. |
| 6–8 | Spring physics on all interactions. Magnetic hover. Staggered entry. Scroll reveals. |
| 9–10 | Cinematic. Framer Motion layout animations. Perpetual micro-animations. Full scroll orchestration. |

**At intensity > 5:** Use Framer Motion `useMotionValue` and `useTransform` — never React `useState` for continuous animations. `staggerChildren` must be in the same Client Component tree as its children.

### VISUAL_DENSITY Scale

| Level | Behavior |
|-------|----------|
| 1–3 | Art gallery. Massive whitespace. Single focal point per section. |
| 4–6 | Balanced. Normal section padding. Standard information hierarchy. |
| 7–10 | Dense. At density > 7: generic card containers are banned. Use `border-t`, `divide-y`, or negative space for grouping. |

---

## Architecture Rules (Always Active)

### Dependency Verification (Mandatory)
Before importing ANY third-party library, check `package.json`. If missing, output the install command before the code. Never assume a library exists.

### Framework Defaults
- React or Next.js. Default to Server Components (RSC).
- RSC safety: global state only in Client Components. Wrap providers in `"use client"` components.
- Interactivity isolation: if motion is active, extract interactive components as isolated leaf components with `'use client'` at top.
- State: local `useState`/`useReducer` for isolated UI. Global state only for deep prop-drilling avoidance.

### Styling
- Tailwind CSS (v3 or v4). Check version before modifying config.
- v4: do NOT use `tailwindcss` plugin in `postcss.config.js`. Use `@tailwindcss/postcss` or the Vite plugin.
- Never complex flex percentage math (`w-[calc(33%-1rem)]`). Always CSS Grid.
- Container: `max-w-[1400px] mx-auto` or `max-w-7xl`.

### Viewport
- Never `h-screen` for hero sections. Always `min-h-[100dvh]` — prevents iOS Safari viewport jumping.
- Standardize breakpoints: `sm`, `md`, `lg`, `xl`.

### Icons
Import path: exactly `@phosphor-icons/react` or `@radix-ui/react-icons`. Standardize `strokeWidth` globally (`1.5` or `2.0` — pick one).

### Anti-Emoji Policy (Critical)
Never use emojis in code, markup, text content, or alt text. Replace with Phosphor or Radix icons, or SVG primitives.

---

## Design Rules

### Typography
- Display/headlines: `text-4xl md:text-6xl tracking-tighter leading-none`
- For premium/creative: `Geist`, `Outfit`, `Cabinet Grotesk`, or `Satoshi` — not Inter
- Dashboard/software: serif fonts are banned. Use `Geist` + `Geist Mono` or `Satoshi` + `JetBrains Mono`
- Body: `text-base text-gray-600 leading-relaxed max-w-[65ch]`

### Color
- Max 1 accent color. Saturation < 80%.
- The AI Purple/Blue gradient is banned. No purple button glows, no neon gradients.
- Absolute neutral bases (Zinc/Slate) + one high-contrast accent (Emerald, Electric Blue, Deep Rose).
- Never mix warm and cool grays in the same project.

### Interaction States (Always Generate All Four)
Claude naturally generates only the success state. Always implement the full cycle:
- **Loading:** Skeleton loaders matching layout dimensions. No generic spinners.
- **Empty:** Composed empty states with a clear path to populate data.
- **Error:** Inline error reporting. Never `window.alert()`.
- **Active/press:** `scale-[0.98]` or `-translate-y-[1px]` on `:active`.

### Forms
Label above input. Error text below input. `gap-2` between input blocks.

---

## Performance Rules

- Never animate `top`, `left`, `width`, `height`. Only `transform` and `opacity`.
- Grain/noise: fixed `pointer-events-none` pseudo-elements only. Never on scrolling containers.
- `backdrop-blur`: never on scrolling containers. Fixed/sticky elements only.
- Never arbitrary `z-50` or `z-[9999]`. Systemic z-index layers only.
- Perpetual animations: memoize with `React.memo`, isolate in their own Client Component. Never trigger parent re-renders.
- Cleanup: every `useEffect` animation needs a cleanup function.

---

## Pre-Flight Checklist

Before outputting code:

- [ ] Global state used only to avoid deep prop-drilling, not arbitrarily
- [ ] Mobile collapse guaranteed — `w-full`, `px-4`, `max-w-7xl mx-auto` at high variance
- [ ] Full-height sections use `min-h-[100dvh]`, not `h-screen`
- [ ] `useEffect` animations have cleanup functions
- [ ] Empty, loading, and error states provided
- [ ] Cards omitted in favor of spacing where `VISUAL_DENSITY < 7`
- [ ] CPU-heavy perpetual animations isolated in their own Client Components
- [ ] No emojis anywhere
