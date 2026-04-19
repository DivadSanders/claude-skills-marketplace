---
name: redesign-existing-projects
description: "When the user wants to upgrade, improve, or audit an existing website or codebase. Use when the user mentions 'redesign,' 'upgrade this,' 'this looks generic,' 'make this look better,' 'improve the design,' 'audit my UI,' 'fix the styling,' 'it looks like an AI built it,' 'polish this,' or pastes existing code and wants it improved."
category: design
tags: [redesign, UI-upgrade, audit, CSS, React, Tailwind, refactor, polish]
version: 2.0.0
author: DivadSanders
---

# Redesign Existing Projects

> Upgrade existing code to premium quality without breaking what works.

## What This Does

Turns Claude into a senior design engineer who systematically audits an existing codebase, diagnoses every generic or weak pattern, and applies targeted upgrades — working with your current stack, not around it.

## When to Use

- You have a working site or component and want it to look significantly better
- You know something looks off but can't diagnose it
- You want a structured audit before deciding what to prioritize
- You just got a Claude-generated UI and it looks generic — this fixes it

## Example Prompts

- "Audit my landing page and tell me what's making it look generic"
- "Upgrade this React component — it looks like a template"
- "Here's my pricing page. Fix the top 5 design problems"

---

## Process

When applied to an existing project:

1. **Scan** — Read the codebase. Identify the framework, styling method (Tailwind, vanilla CSS, styled-components), and current patterns.
2. **Diagnose** — Run through the full audit below. List every generic pattern, weak point, and missing state.
3. **Prioritize** — Order fixes by impact (see Fix Priority below).
4. **Fix** — Apply targeted upgrades within the existing stack. Don't rewrite from scratch.

---

## Rules

- Work with the existing tech stack. Never migrate frameworks or styling libraries.
- Never break existing functionality. Verify after each change.
- Check `package.json` before importing any new library.
- If the project uses Tailwind, check the version (v3 vs v4) before modifying config.
- Small, targeted improvements over big rewrites.

---

## The Full Audit

### Typography

| Problem | Fix |
|---------|-----|
| Browser defaults or Inter everywhere | Replace with `Geist`, `Outfit`, `Cabinet Grotesk`, or `Satoshi`. Pair serif headers with sans-serif body for editorial feel. |
| Headlines lack presence | Increase display size, tighten `letter-spacing`, reduce `line-height`. Headlines should feel heavy and intentional. |
| Body text too wide | Max `~65ch` paragraph width. Increase `line-height` for readability. |
| Only Regular (400) and Bold (700) weights | Introduce Medium (500) and SemiBold (600) for subtler hierarchy. |
| Numbers in proportional font | Use `font-variant-numeric: tabular-nums` for data-heavy interfaces. |
| All-caps subheaders everywhere | Try lowercase italics, sentence case, or small-caps. |
| Orphaned single words on last line | Fix with `text-wrap: balance` or `text-wrap: pretty`. |

### Color and Surfaces

| Problem | Fix |
|---------|-----|
| Pure `#000000` background | Replace with `#0a0a0a`, `#121212`, or a tinted dark. |
| Oversaturated accents | Keep saturation below 80%. |
| More than one accent color | Pick one. Remove the rest. |
| Mixing warm and cool grays | One gray family. Consistent hue throughout. |
| Purple/blue "AI gradient" aesthetic | This is the most common AI fingerprint. Replace with neutral base + single considered accent. |
| Generic `box-shadow` | Tint shadows to match background hue — not pure black at low opacity. |
| Perfectly flat design, zero texture | Add subtle noise, grain, or micro-patterns. Pure flat feels sterile. |
| Random dark section in a light-mode page | Either commit to full dark mode or use a slightly darker shade of the same palette. |
| Empty flat sections with no depth | Add background imagery, patterns, or ambient gradients. Even `opacity: 0.05` on an image adds presence. |

### Layout

| Problem | Fix |
|---------|-----|
| Everything centered and symmetrical | Break symmetry with offset margins, mixed aspect ratios, or left-aligned headers. |
| Three equal card columns as feature row | Most generic AI layout. Replace with 2-column zig-zag, asymmetric grid, horizontal scroll, or masonry. |
| `height: 100vh` for full-screen sections | Replace with `min-height: 100dvh` — fixes iOS Safari viewport jumping. |
| Complex flexbox percentage math | Replace with CSS Grid. |
| No max-width container | Add `~1200–1440px` container with auto margins. |
| Uniform border-radius | Vary radius: tighter on inner elements, softer on containers. |
| No overlap or depth | Use negative margins to create layering. |
| Missing whitespace | Double the spacing. Dense layouts work for data dashboards, not marketing pages. |
| Buttons not bottom-aligned across cards | Pin CTAs to card bottom so they form a clean horizontal line regardless of content above. |

### Interactivity and States

| Problem | Fix |
|---------|-----|
| No hover states on buttons | Add background shift, slight scale, or translate. |
| No active/pressed feedback | `scale(0.98)` or `translateY(1px)` on press. |
| Instant transitions, zero duration | `200–300ms` smooth transitions on all interactive elements. |
| Missing focus ring | Visible focus indicators are an accessibility requirement, not optional. |
| Generic circular loading spinners | Replace with skeleton loaders that match the layout shape. |
| No empty states | Design a composed "getting started" view for empty dashboards and lists. |
| No error states | Clear, inline error messages for forms. Never `window.alert()`. |
| No current page indicator in nav | Style the active nav link differently. |
| Animations on `top`, `left`, `width`, `height` | Switch to `transform` and `opacity` for GPU-accelerated animation. |

### Content

| Problem | Fix |
|---------|-----|
| "John Doe," "Jane Smith," "Acme Corp" | Use diverse, realistic names. |
| Round fake numbers (`99.99%`, `$100.00`) | Use organic, messy data: `47.2%`, `$99.00`. |
| AI clichés: "Elevate," "Seamless," "Unleash," "Game-changer" | Write plain, specific language. |
| Exclamation marks in success messages | Remove. Be confident, not loud. |
| "Oops!" error messages | Be direct: "Connection failed. Please try again." |
| Lorem Ipsum anywhere | Write real draft copy. |
| Title Case On Every Header | Use sentence case. |

### Component Patterns

| Problem | Fix |
|---------|-----|
| Generic card (border + shadow + white bg) | Remove border, or only background, or only spacing. Cards only when elevation communicates hierarchy. |
| 3-card carousel testimonials with dots | Replace with masonry wall, embedded posts, or single rotating quote. |
| Pill "New" and "Beta" badges | Try square badges or plain text labels. |
| Accordion FAQ sections | Use side-by-side list or inline progressive disclosure. |
| Pricing table with 3 equal towers | Highlight recommended tier with color and emphasis — not just extra height. |
| Modals for simple actions | Use inline editing, slide-overs, or expandable sections. |
| Footer link farm with 4 columns | Simplify to main nav paths and legally required links. |

### Iconography

| Problem | Fix |
|---------|-----|
| Lucide or Feather exclusively | Use Phosphor or Heroicons for differentiation. |
| Rocketship for "Launch," shield for "Security" | Replace cliché metaphors: bolt, fingerprint, spark, vault. |
| Inconsistent stroke widths | Standardize to one stroke weight across all icons. |
| Missing favicon | Always include a branded favicon. |

### Strategic Omissions (What AI Typically Forgets)

- No legal links → add privacy policy and terms to footer
- No "back" navigation → every page needs a way back
- No custom 404 page → design a helpful branded experience
- No form validation → add client-side validation
- No `<title>`, `description`, `og:image` meta tags → add them

---

## Fix Priority

Apply in this order for maximum visual impact, minimum risk:

1. **Font swap** — biggest instant improvement, lowest risk
2. **Color palette cleanup** — remove clashing or oversaturated colors
3. **Hover and active states** — makes the interface feel alive
4. **Layout and spacing** — proper grid, max-width, consistent padding
5. **Replace generic components** — swap cliché patterns for better alternatives
6. **Add loading, empty, and error states** — makes it feel finished
7. **Polish typography scale** — the premium final touch
