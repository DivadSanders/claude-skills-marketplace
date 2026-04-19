---
name: minimalist-ui
description: "When the user wants to build a clean, editorial, warm-monochrome UI — no gradients, no generic SaaS look, no heavy shadows. Use when the user mentions 'minimalist,' 'editorial,' 'clean design,' 'Notion-style,' 'Linear-style,' 'monochrome,' 'document-style interface,' or wants something that looks expensive without looking loud."
category: design
tags: [UI, frontend, minimalist, editorial, design-system, CSS, React, HTML]
version: 2.0.0
author: DivadSanders
---

# Minimalist UI

> Editorial, warm-monochrome interfaces. High typographic contrast, flat bento grids, muted pastel accents. The anti-SaaS aesthetic.

## What This Does

Overrides Claude's default tendency toward generic, gradient-heavy, icon-packed SaaS UI. Instead enforces a premium editorial design system: warm off-whites, careful typography, bento grid layouts, and zero visual noise. Think Notion, Linear, or Loom — but distinctly yours.

## When to Use

- You want a UI that looks considered and calm, not corporate and cluttered
- You're building a product, dashboard, or landing page and want it to feel premium without loud branding
- You're tired of Claude generating the same Inter-font, blue-CTA, three-column card layout every time

## Example Prompts

- "Build a settings page in this style for a SaaS app"
- "Design a pricing page using minimalist editorial UI"
- "Create a clean dashboard layout with warm tones and no shadows"

---

## Absolute Constraints

These are non-negotiable. Never violate them:

**Banned fonts:** Inter, Roboto, Open Sans  
**Banned icons:** Lucide, Feather, standard Heroicons (thin-line generics)  
**Banned shadows:** Tailwind's `shadow-md`, `shadow-lg`, `shadow-xl` — any heavy drop shadow  
**Banned colors:** Bright primary backgrounds (blue hero sections, green CTAs)  
**Banned effects:** Gradients, neon colors, 3D glassmorphism  
**Banned shapes:** `rounded-full` on large containers, cards, or primary buttons  
**Banned content:** Emojis anywhere in markup or text. Replace with proper icons or SVG.  
**Banned copy:** "Elevate," "Seamless," "Unleash," "Next-Gen," "Game-changer," "Delve." Use plain, specific language.  
**Banned placeholders:** "John Doe," "Acme Corp," "Lorem Ipsum." Use realistic, contextual content.

---

## Typography

Extreme typographic contrast is the primary design tool.

**Primary sans-serif (body, UI, buttons):**
`font-family: 'SF Pro Display', 'Geist Sans', 'Helvetica Neue', 'Switzer', sans-serif`

**Editorial serif (hero headings, pull quotes):**
`font-family: 'Lyon Text', 'Newsreader', 'Playfair Display', 'Instrument Serif', serif`  
Apply: `letter-spacing: -0.02em` to `-0.04em`, `line-height: 1.1`

**Monospace (code, keystrokes, metadata):**
`font-family: 'Geist Mono', 'SF Mono', 'JetBrains Mono', monospace`

**Text colors:**
- Body: `#111111` or `#2F3437` (never pure `#000000`)
- Secondary: `#787774`
- Line height for body: `1.6`

---

## Color Palette

Color is a scarce resource. Use it only for semantic meaning or subtle accents.

| Role | Value |
|------|-------|
| Background | `#FFFFFF` or `#F7F6F3` / `#FBFBFA` |
| Card surface | `#FFFFFF` or `#F9F9F8` |
| Borders / dividers | `#EAEAEA` or `rgba(0,0,0,0.06)` |

**Accent colors — muted pastels only:**
| Color | Background | Text |
|-------|-----------|------|
| Red | `#FDEBEC` | `#9F2F2D` |
| Blue | `#E1F3FE` | `#1F6C9F` |
| Green | `#EDF3EC` | `#346538` |
| Yellow | `#FBF3DB` | `#956400` |

---

## Components

**Bento grid cards:**
- Asymmetrical CSS Grid layouts
- Border: exactly `1px solid #EAEAEA`
- Border radius: `8px` or `12px` maximum
- Internal padding: `24px` to `40px`

**Primary CTA buttons:**
- Background `#111111`, text `#FFFFFF`
- Border radius: `4px` to `6px`
- No box-shadow
- Hover: shift to `#333333` or `transform: scale(0.98)`

**Tags and status badges:**
- Pill-shaped (`border-radius: 9999px`)
- Small type (`text-xs`), uppercase, wide tracking (`letter-spacing: 0.05em`)
- Background: muted pastels from the palette above

**Accordions (FAQ):**
- No container boxes. Separate items with `border-bottom: 1px solid #EAEAEA` only
- Toggle icon: clean `+` / `−`, nothing else

**Keyboard shortcut micro-UI:**
- Use `<kbd>` tags
- Style: `border: 1px solid #EAEAEA`, `border-radius: 4px`, `background: #F7F6F3`, monospace font

**Software mockup chrome:**
- Top bar: white, three small light-gray circles (macOS window controls)
- Keep the frame minimal — it should frame, not compete with, the content inside

---

## Iconography and Imagery

**Icons:** Phosphor Icons (Bold or Fill weight) or Radix UI Icons. Standardize stroke width across all icons in a given UI.

**Photography:** Desaturated, warm-toned. Apply subtle warm overlay. Never oversaturated stock photos. Use `https://picsum.photos/seed/{context}/1200/800` as placeholder.

**Backgrounds:** Sections should not feel empty. Use subtle full-width imagery at low opacity, soft radial warm light (`radial-gradient` at `opacity: 0.03`), or minimal geometric line patterns.

---

## Motion

Motion should feel present but invisible — never decorative.

**Scroll entry:** `translateY(12px)` + `opacity: 0` → `translateY(0)` + `opacity: 1` over `600ms` with `cubic-bezier(0.16, 1, 0.3, 1)`. Use `IntersectionObserver`. Never `window.addEventListener('scroll')`.

**Card hover:** Transition from zero shadow to `0 2px 8px rgba(0,0,0,0.04)` over `200ms`.

**Button press:** `transform: scale(0.98)` on `:active`.

**Staggered reveals:** `animation-delay: calc(var(--index) * 80ms)` on list/grid items.

**Performance rules:**
- Animate ONLY via `transform` and `opacity` — never `top`, `left`, `width`, `height`
- `will-change: transform` only on elements that are actively animating
- Grain/noise overlays: `position: fixed; pointer-events: none` only — never on scrolling containers

---

## Execution Checklist

Before outputting any UI code:

1. Establish macro-whitespace first: `py-24` or `py-32` between sections
2. Constrain content width: `max-w-4xl` or `max-w-5xl`
3. Apply typographic hierarchy and monochromatic color variables
4. Every card, divider, border: `1px solid #EAEAEA`
5. Scroll entry animations on all major content blocks
6. Add visual depth via imagery, ambient gradients, or subtle texture — no empty flat backgrounds
7. Check all banned elements are absent
