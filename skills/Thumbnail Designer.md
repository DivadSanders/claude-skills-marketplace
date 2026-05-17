---
name: Thumbnail Designer
description: >
  Generate a brand-consistent cover image or thumbnail for a blog post, Substack article,
  or newsletter. Use this skill when the user asks for a thumbnail, cover image, hero image,
  article visual, or social preview for a written piece.
  Also trigger when the user says "make a cover for this post", "generate a thumbnail",
  "I need a header image for this article", "create a visual for this", or pastes a draft
  and asks for an image to go with it.
  This skill reads the article, designs a scene that visualizes its core argument,
  and generates the image by calling the Gemini image API via a local Node script.
  For Claude Code only — requires Bash, Node.js 18+, and a Gemini API key.
category: creative
tags: [image-generation, thumbnail, cover-image, Gemini, Claude-Code, branding, Substack, visual]
version: 1.0.0
author: DivadSanders
---

# Thumbnail Designer

> Read the article. Design the scene. Generate the cover — brand-consistent, every time.

## What This Does

Turns any article or draft into a brand-consistent cover image. Instead of describing what the article is *about*, this skill extracts what it *argues* — the actual cause-effect or insight — and designs a visual scene that shows that finding. The scene is built against your personal BRAND BLOCK: your characters, illustration style, composition rules, and constraints. Once the scene plan is approved, it calls the Gemini image API via a local Node script and saves the result directly to your output folder.

Every generated image is checked against your brand policies before being delivered. Iteration happens through targeted edits to the existing image, not full regeneration — which preserves consistency and keeps API costs down.

## When to Use

- You've finished a draft and need a cover image before publishing
- You want a thumbnail for a Substack post, blog article, or newsletter
- You need multiple visual variants of the same scene to compare
- You want to iterate on an existing cover without starting over

**Not for:** animated content, video covers, photo-realistic photography, or images requiring extensive legible text.

**Claude Code only.** This skill uses Bash to invoke `generate.js`, a local Node script in your writing project directory. It will not run in Claude.ai — Bash is required.

## Example Prompts

- "Make a cover image for this article: [paste draft]"
- "Generate a thumbnail for this post in my brand style"
- "I need a hero image for this piece — here's the draft"
- "Create 3 variants of a cover for this article so I can pick one"
- "Edit the last thumbnail — remove the background and keep everything else"

---

## Prerequisites (One-Time Setup)

Before this skill can run, complete these steps once:

1. **Gemini API key** with billing enabled — stored in `.env` as `GOOGLE_AI_API_KEY=...` in your project directory, or exported in your shell rc file
2. **`generate.js` in your project directory** — the zero-dependency Node script that calls the Gemini API
3. **Node.js 18+** installed
4. **BRAND BLOCK filled in below** — every `[FILL IN ...]` marker replaced with your actual brand details

If the BRAND BLOCK still contains `[FILL IN]` markers, stop and tell the user the skill hasn't been customized yet. They need to edit `~/.claude/skills/cover-image-studio/SKILL.md` and replace every placeholder. If `generate.js` is missing or the API key isn't set, the script's error output will identify the specific problem.

---

## BRAND BLOCK

> This is the single source of truth for every cover image. Fill it in once. Only update it when your visual identity changes — not per article.

### Characters

**Primary character:**
`[FILL IN — 1-3 sentences. Include: gender/age range, distinctive physical features, clothing or accessories, and the illustration style they're rendered in.]`

**Secondary character (optional):**
`[FILL IN — describe similarly, or leave blank if you don't use a recurring second character.]`

**Reference image paths:**
- Primary character: `[FILL IN — absolute path]`
- Secondary character: `[FILL IN — absolute path, or leave blank]`
- Style anchor (an image that shows the illustration style you want): `[FILL IN — absolute path]`

### Canvas

**Aspect ratio:** `[FILL IN — e.g. 16:9, 4:3, 1:1, 3:2]`

**Pixel dimensions:** `[FILL IN — e.g. 1456×816, 1200×630, 1080×1080]`

**Output folder:** `[FILL IN — absolute path where generated images should be saved]`

### Composition Policies

**Illustration style:**
`[FILL IN — be concrete: line weight (thin/medium/heavy), color treatment (flat / soft shading / gradients / watercolor), palette (saturated / muted / pastel / monochrome), level of detail.]`

**Background:**
`[FILL IN — e.g. "Pure white, no environment" / "Subtly blurred scene hinting at the article's domain" / "Abstract gradient in brand colors" / "Whatever fits the article tone"]`

**Maximum element count:**
`[FILL IN — e.g. "3 max: primary + secondary + 1 prop" / "5-6 elements OK" / "No fixed limit, judge per article"]`

**Environment policy:**
`[FILL IN — e.g. "Never — figures on plain background" / "Always — figures inhabit a scene relevant to the article" / "Optional based on article tone"]`

**Text in image:**
`[FILL IN — e.g. "Forbidden anywhere" / "Title text in lower third only" / "Labels on objects allowed when integral" / "No constraint"]`

**Prop style:**
`[FILL IN — e.g. "Domain-native — only objects the article's subjects would actually touch" / "Symbolic icons — recognizable visual metaphors" / "Abstract/geometric forms" / "Photographic real-world objects"]`

**Banned elements:**
`[FILL IN — list anything you never want, or leave blank. E.g. "no charts or data viz" / "no real-world brand logos" / "no children"]`

---

## Workflow

### Step 1 — Read the Article

Identify three things:

- **Core finding** — the one cause-effect or insight the article is arguing. Not the topic — the *finding*. ("Flattery makes a model skip planning" is a finding. "AI politeness research" is just a topic.)
- **Tone** — confident, skeptical, alarmed, hopeful, technical, warm, etc.
- **Concrete domain objects** — physical things that appear in the article's actual subject. Cooking → ingredients, utensils. Coding → terminals, code. Finance → charts, contracts. These are candidate props.

---

### Step 2 — Design the Scene

Design a single coherent scene within the BRAND BLOCK constraints. Output this plan before generating anything:

```
SCENE PLAN
- Core finding (1 sentence): ...
- Composition: <where each character is positioned, where the prop is, what surrounds them — within BRAND BLOCK background/environment/element-count policies>
- Prop: <one specific object — selected using the BRAND BLOCK prop style>
- Action / state shown: <what the figures are DOING that conveys the finding — not posing, acting>
- Why this works: <one sentence connecting the visual to the core finding>
```

---

### Step 3 — Confirm Before Generating

Each call to `generate.js` is a paid API call. Scene planning in text is free. Always show the SCENE PLAN and ask for approval before generating.

**If the article has multiple strong angles**, offer choices:

- **Multiple scene variants** — propose 2–3 different framings (the cause, the effect, the surprise, the human element, the takeaway). User picks one to render. Cheapest path.
- **Multiple image variants of one scene** — same prompt, different renders. Useful when the plan is right but you want visual options. Run `generate.js` N times with the same prompt, different output filenames.
- **Both** — pick a plan first, then render variants of it.

**Don't decide the number of images for the user.** Look up the current per-image price for their chosen model at [https://ai.google.dev/gemini-api/docs/pricing](https://ai.google.dev/gemini-api/docs/pricing) — pricing shifts over time, so don't quote a hardcoded number. Tell them the actual current rate and let them decide how many to generate.

---

### Step 4 — Generate via Bash

Build the full prompt using the PROMPT TEMPLATE below, then call `generate.js` from the project directory:

```bash
node generate.js \
  --prompt="<full prompt with scene description and constraints>" \
  --refs="<primary character path>,<secondary character path>,<style anchor path>" \
  --output="<output_folder>/<article-slug>-YYYY-MM-DD.png"
```

The `--refs` argument is a comma-separated list of absolute paths from the BRAND BLOCK. Omit secondary character if blank.

**For multiple variants of the same scene**, call `generate.js` once per variant with the same `--prompt` and `--refs` but a different `--output` filename. Run sequentially, not in parallel, to avoid rate limits. Use suffixes: `<slug>-v1.png`, `<slug>-v2.png`, `<slug>-v3.png`.

On success, the script prints `OK: <output_path>`.

If you see `GOOGLE_AI_API_KEY is not set`, the `.env` file is missing. Tell the user to run:
```bash
echo 'GOOGLE_AI_API_KEY=your-key' > .env
```
then retry.

---

### Step 5 — Review Against Brand Policies

Use the `Read` tool to view the generated image. Check every policy:

- ✓/✗ Background matches BRAND BLOCK background policy?
- ✓/✗ Element count within BRAND BLOCK maximum?
- ✓/✗ Environment matches BRAND BLOCK environment policy?
- ✓/✗ Text policy honored?
- ✓/✗ Prop matches BRAND BLOCK prop style?
- ✓/✗ No banned elements present?
- ✓/✗ Characters match brand reference images?
- ✓/✗ Aspect ratio and canvas dimensions correct?

Flag any failures and propose a targeted edit before delivering.

---

### Step 6 — Iterate via Edit, Not Regenerate

When changes are needed, edit the existing image rather than starting over:

```bash
node generate.js \
  --input="<previous output path>" \
  --prompt="<edit instructions: what to change AND what to preserve>" \
  --output="<new output path>"
```

Editing preserves character consistency, style, and composition between iterations. Regenerating produces a fresh image that may drift from the brand in unwanted ways. Each edit is one paid API call.

Always specify both what to change **and** what to preserve. "Make it better" does not work.

---

## Prompt Template

Use this skeleton for the `--prompt` argument — substitute values from the article and BRAND BLOCK:

```
Generate a single illustrated frame in the EXACT style of the reference images,
featuring the EXACT characters from the references.

Scene to render:
<your scene description from Step 2>

Style and constraints (violating any = wrong output):
- Illustration style: <BRAND illustration style>
- Background: <BRAND background policy>
- Aspect ratio: <BRAND aspect ratio> — state this twice if needed
- Primary character must look identical to the first reference image
- <Secondary character must look identical to the second reference image — only if applicable>
- Match the style anchor's line weights, palette, and shading exactly
- Text in image: <BRAND text policy>
- Element count: stay within <BRAND max element count>
- Banned elements: <BRAND banned elements, if any>
```

Pass references via `--refs` in this order: primary character, secondary character (if used), style anchor.

---

## Universal Image Principles

These apply regardless of brand — they're what separates a polished cover from a generic one:

**One coherent scene, not a collage.** All elements should share the same lighting, scale, and illustration style. Avoid the "transparent PNG cutouts pasted on a background" look unless your brand explicitly calls for it.

**Characters must match brand references.** Always pass reference images via `--refs`. Add specific physical descriptions to the prompt to reinforce them — references alone drift slightly.

**The prop should enact the finding, not just symbolize it.** Whatever prop style your brand uses, the prop should *do something* that shows the article's cause-effect. A shrinking stack of paperwork tells more story than a static one. A wilting plant says more than a healthy one.

**Specificity beats vagueness in prompts.** "A stack of papers" is vague. "A tall stack of yellow sticky notes visibly shrinking from left to right" is specific. Concrete descriptions produce on-target results.

**Two-element comparisons count as one prop slot.** When an article hinges on a contrast (before/after, honest vs. gamed, A vs. B), a tightly-coupled prop pair is fine. It counts as one element for element-count purposes.

---

## Common Pitfalls

| Problem | What Happens | Fix |
|---|---|---|
| **Environment leak** | Even with "no environment" rules, Gemini adds a desk, bookshelf, or floor | Edit with `--input`: "Remove the [specific element]. Background should be [BRAND policy]. Keep everything else identical." |
| **Text bleed-through** | Gemini renders text on signs, screens, or paper despite "no text" rules | Edit: "Remove all text, letters, and numbers from [element]. Replace with abstract squiggles or blank texture. Keep everything else identical." |
| **Character drift** | Slight face-shape, hair-color, or proportion drift between iterations | Add more specific physical-feature description to the prompt. If severe, regenerate from scratch — editing won't fix identity. |
| **Aspect ratio ignored** | Gemini ignores the ratio | State it twice in the prompt |
| **"Atmospheric" background adds environment** | Vague atmospheric language causes Gemini to hallucinate a scene | Stick to concrete physical descriptions. Avoid "subtle," "moody," "atmospheric" if your brand background is plain. |
| **Edit deletes more than intended** | "Remove the red marks" removes the object the marks were on | Always state what to preserve alongside what to remove |

---

## Cost Notes

Each `generate.js` call = one API call, billed at the current per-image rate for the model configured. Scene planning (text conversation) is free.

Pricing varies significantly by model — cheaper flash models vs. pro models can differ by an order of magnitude. Always look up the actual current rate at [https://ai.google.dev/gemini-api/docs/pricing](https://ai.google.dev/gemini-api/docs/pricing) before telling the user how much something costs. Never quote a hardcoded price — rates change.

The user decides how many images to generate. Never make that decision for them.

---

## Completion Checklist

- [ ] Article read and core finding identified (not just the topic — the actual argument)
- [ ] SCENE PLAN written and shown to user before any generation
- [ ] User confirmed scene plan (or chose from variants)
- [ ] Number of images and cost confirmed with user
- [ ] `generate.js` called with correct `--prompt`, `--refs`, and `--output`
- [ ] Generated image reviewed against all BRAND BLOCK policies
- [ ] Any policy violations flagged and edited before delivery
- [ ] Final image path reported to user
- [ ] Iteration used `--input` edit mode (not full regeneration) where possible
