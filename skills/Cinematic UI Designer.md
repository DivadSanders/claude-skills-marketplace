---
name: Cinematic Designer
description: "When the user wants to build agency-level, premium UI — with cinematic motion, haptic depth, and Awwwards-tier aesthetics. Use when the user mentions 'premium design,' 'agency quality,' 'high-end UI,' 'Vercel-style,' 'Linear-style,' 'Awwwards,' 'micro-animations,' 'glass morphism,' 'dark mode,' 'expensive-looking,' or 'make it look like a $150k agency built it.'"
category: design
tags: [UI, premium, agency-level, motion, React, Tailwind, dark-mode, micro-interactions, awwwards]
version: 2.0.0
author: DivadSanders
---

# Cinematic Designer

> Agency-level digital experiences. Haptic depth, cinematic motion, obsessive micro-interactions — never the same layout twice.

## What This Does

Gives Claude the design sensibility, banned-pattern awareness, and execution process of a senior agency UI engineer. Every output pulls from a variance engine that mixes layout archetypes, texture profiles, and motion choreography — so nothing looks like a template.

## When to Use

- You want UI that looks like it cost $150k to build
- You're building a SaaS product, marketing site, or feature page and want cinematic quality
- You keep getting the same Inter-font, blue-gradient, Bootstrap-grid output from Claude
- You want specific motion physics, not generic CSS transitions

## Example Prompts

- "Build a dark-mode SaaS hero section with glass cards and magnetic hover buttons"
- "Create an editorial split-screen landing page for an AI product"
- "Design a bento grid feature section with perpetual micro-animations"

---

## The Absolute Zero List

If any of the following appear in generated code, the design fails immediately:

**Banned fonts:** Inter, Roboto, Arial, Open Sans, Helvetica  
**Banned icons:** Standard Lucide, FontAwesome, Material Icons (thick-stroked generics). Use only ultra-precise lines: Phosphor Light, Remix Line.  
**Banned borders/shadows:** Generic `1px solid gray`. Harsh dark shadows (`shadow-md`, `rgba(0,0,0,0.3)`).  
**Banned layouts:** Edge-to-edge sticky navbars. Symmetrical 3-column Bootstrap grids without massive whitespace.  
**Banned motion:** `linear` or `ease-in-out` transitions. Any instant state change without interpolation.  

Assume premium fonts (`Geist`, `Clash Display`, `PP Editorial New`, `Plus Jakarta Sans`) are available.

---

## The Variance Engine

Before writing any code, silently select one combination from each archetype. Never generate the same combination twice in a row.

### Vibe Archetypes (pick one)

**1. Ethereal Glass** — for SaaS / AI / Tech  
Deepest OLED black (`#050505`). Radial mesh gradient orbs (subtle purple/emerald) in background. Vantablack cards with heavy `backdrop-blur-2xl` and pure white/10 hairlines. Wide geometric Grotesk.

**2. Editorial Luxury** — for Lifestyle / Real Estate / Agency  
Warm creams (`#FDFBF7`), muted sage, or deep espresso. High-contrast Variable Serif for massive headings. Subtle CSS noise overlay (`opacity-[0.03]`) for a physical paper feel.

**3. Soft Structuralism** — for Consumer / Health / Portfolio  
Silver-grey or pure white. Massive bold Grotesk. Airy floating components with ultra-soft, highly diffused ambient shadows.

### Layout Archetypes (pick one)

**1. Asymmetrical Bento**  
Masonry-like CSS Grid with varying card sizes (`col-span-8 row-span-2` next to stacked `col-span-4`). Breaks visual monotony.  
*Mobile:* Single-column stack. Reset all `col-span` to `col-span-1`.

**2. Z-Axis Cascade**  
Elements stacked like physical cards, slightly overlapping, some with subtle `-2deg` / `3deg` rotation.  
*Mobile:* Remove all rotations and negative-margin overlaps below `768px`. Stack vertically.

**3. Editorial Split**  
Massive typography left (`w-1/2`). Scrollable horizontal image pills or staggered interactive cards right.  
*Mobile:* Full-width vertical stack. Typography block on top.

**Universal mobile rule:** Any asymmetric layout above `md:` MUST fall back to `w-full`, `px-4`, `py-8` below `768px`. Never use `h-screen` — always `min-h-[100dvh]`.

---

## Component Architecture

### The Double-Bezel (Doppelrand)
Never place a card flatly on the background. Create nested enclosures that feel like physical hardware:

**Outer shell:** `bg-black/5` or `bg-white/5` background, `ring-1 ring-black/5` hairline, `p-1.5` padding, `rounded-[2rem]`.  
**Inner core:** Its own background color, inner highlight `shadow-[inset_0_1px_1px_rgba(255,255,255,0.15)]`, radius calculated as `rounded-[calc(2rem-0.375rem)]`.

### Button-in-Button (Nested CTA)
Primary buttons are rounded pills (`rounded-full`, `px-6 py-3`). If a button has an arrow icon, it lives inside its own circular wrapper `w-8 h-8 rounded-full bg-black/5 flex items-center justify-center` — never naked next to the text.

### Spatial Rhythm
- Section padding minimum: `py-24`. Target: `py-32` to `py-40`.
- Eyebrow tags before H1/H2s: `rounded-full px-3 py-1 text-[10px] uppercase tracking-[0.2em] font-medium`

---

## Motion Choreography

All transitions use custom cubic-bezier. No defaults. Target: `cubic-bezier(0.32, 0.72, 0, 1)` with `duration-700`.

### Floating Nav
- Default: glass pill floating from top — `mt-6`, `mx-auto`, `w-max`, `rounded-full`
- Hamburger morph: 2–3 lines rotate/translate to form `×` (`rotate-45` / `-rotate-45` with absolute positioning)
- Open state: screen-filling overlay with `backdrop-blur-3xl bg-black/80`
- Nav link reveals: staggered mask — `translate-y-12 opacity-0` → `translate-y-0 opacity-100`, delays: `100ms`, `150ms`, `200ms` per item

### Magnetic Buttons (hover physics)
On hover: don't just change background. Scale down on press (`active:scale-[0.98]`). Inner icon circle translates diagonally (`group-hover:translate-x-1 group-hover:-translate-y-[1px]`) and scales up (`scale-105`).

### Scroll Entry Animations
Elements never appear statically. Entering the viewport: `translate-y-16 blur-md opacity-0` → `translate-y-0 blur-0 opacity-100` over `800ms+`. Use `IntersectionObserver` or Framer Motion `whileInView`. Never `window.addEventListener('scroll')`.

---

## Performance Rules

- **GPU-safe only:** Animate exclusively via `transform` and `opacity`. Never `top`, `left`, `width`, `height`.
- **Blur constraints:** `backdrop-blur` only on fixed or sticky elements. Never on scrolling containers — continuous GPU repaints, severe mobile frame drops.
- **Grain overlays:** `position: fixed; pointer-events: none` pseudo-elements only. Never on scrolling content.
- **Z-index:** No `z-50` spam. Systemic layers only: sticky nav, modals, overlays, tooltips.
- **`will-change: transform`:** Only on elements actively animating.

---

## Pre-Output Checklist

Before delivering any code, verify:

- [ ] No banned fonts, icons, borders, shadows, layouts, or motion patterns
- [ ] A Vibe Archetype and Layout Archetype were consciously selected
- [ ] All major cards use Double-Bezel nested architecture (outer shell + inner core)
- [ ] CTA buttons use Button-in-Button pattern where applicable
- [ ] Section padding is minimum `py-24`
- [ ] All transitions use custom cubic-bezier curves — no `linear` or `ease-in-out`
- [ ] Scroll entry animations present — no element appears statically
- [ ] Layout collapses to single-column below `768px`
- [ ] All animations use only `transform` and `opacity`
- [ ] `backdrop-blur` only on fixed/sticky elements
- [ ] Output reads as "$150k agency build" — not "nice-looking template"
