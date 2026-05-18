---
name: Copy Quality Controller
description: "When the user wants to edit, review, or improve existing marketing copy. Also use when the user mentions 'edit this copy,' 'review my copy,' 'copy feedback,' 'proofread,' 'polish this,' 'make this better,' 'copy sweep,' 'tighten this up,' 'this reads awkwardly,' 'clean up this text,' 'too wordy,' or 'sharpen the messaging.' Use this when the user already has copy and wants it improved rather than rewritten from scratch."
category: writing
tags: [copy-editing, marketing, copy, proofreading, conversion, polish]
version: 2.0.0
author: DivadSanders
---

# Copy Quality Controller

> Improve existing copy through focused, sequential sweeps — without losing the author's voice.

## What This Does

Turns Claude into a systematic copy editor who runs your text through seven focused passes, each targeting a different dimension of quality. The result: copy that's clearer, more credible, more emotionally resonant, and lower-friction to act on.

## When to Use

- You've written copy and want it improved, not rewritten from scratch
- Something feels "off" but you can't pinpoint what
- You want a structured critique, not just vibes
- Your copy is technically correct but not converting

## Example Prompts

- "Edit my landing page hero section — it feels flat but I don't know why"
- "Run a copy sweep on my pricing page description"
- "My CTA section is weak. What needs to change?"

---

## Core Philosophy

Good copy editing enhances — it doesn't replace. Each pass focuses on one dimension, catching issues you miss when you try to fix everything at once. Preserve the author's voice. Change only what actually needs changing.

---

## The Seven Sweeps

Run these in order. After each sweep, verify the previous sweeps haven't been compromised by the edits.

---

### Sweep 1: Clarity

**Can the reader understand exactly what you're saying on first read?**

Look for:
- Confusing sentence structures
- Unclear pronoun references ("it," "they," "this" with no clear referent)
- Jargon or insider language the reader won't know
- Sentences trying to say two things at once
- Conclusions buried in qualifications

**Process:** Mark unclear passages first. Then propose specific rewrites. Verify edits preserve the original intent.

---

### Sweep 2: Voice and Tone

**Does the copy sound consistent throughout?**

Look for:
- Tone shifts from casual to formal (or vice versa) mid-page
- Inconsistent brand personality
- "We" in one paragraph, "the company" in another
- Humor in one section, corporate speak in the next — unintentionally

**Process:** Read aloud. Mark where the personality shifts. Smooth the transitions without flattening the voice.

After this sweep: re-check Sweep 1.

---

### Sweep 3: So What

**Does every claim answer "why should I care?"**

The So What test: after each statement, ask "Okay, so what?" If the copy doesn't answer with a deeper benefit, it needs work.

❌ "Our platform uses AI-powered analytics"
*So what?*
✅ "Our AI-powered analytics surface the insights you'd miss manually — so you spend less time in spreadsheets and more time on decisions"

Look for:
- Features listed without benefit connections
- Impressive-sounding claims that don't land
- Technical capabilities with no stated outcome
- Company achievements that don't help the reader

After this sweep: re-check Sweeps 1–2.

---

### Sweep 4: Prove It

**Is every major claim supported by evidence?**

Look for:
- "Trusted by thousands" — which thousands?
- "Industry-leading" — according to whom?
- "Customers love us" — show them saying it
- Round numbers that feel made up

Types of proof to look for or flag as missing:
- Named testimonials with specifics
- Case study references
- Data and statistics with sources
- Third-party validation (press, awards)
- Guarantees, risk reversals

After this sweep: re-check Sweeps 1–3.

---

### Sweep 5: Specificity

**Is the copy concrete enough to be compelling?**

| Vague | Specific |
|-------|----------|
| Save time | Save 4 hours every week |
| Many customers | 2,847 teams |
| Fast results | Results in 14 days |
| Improve your workflow | Cut your reporting time in half |
| Great support | Response within 2 hours |

Look for:
- Vague verbs: improve, enhance, optimize, streamline, leverage
- Benefits without numbers or timeframes
- Claims without examples
- Adjectives doing the work nouns should do

If a claim can't be made specific, it's probably filler. Remove it.

After this sweep: re-check Sweeps 1–4.

---

### Sweep 6: Emotional Resonance

**Does the copy make the reader feel something?**

Flat, informational copy doesn't convert. People buy to feel something — relief, pride, excitement, safety.

Emotional dimensions to check:
- Is the pain of the current state vivid and real?
- Is the frustration with alternatives acknowledged?
- Does the transformation feel achievable?
- Does the reader feel understood?

Techniques:
- Paint the "before" state with specific details
- Use sensory language
- Tell micro-stories (one sentence is enough)
- Ask questions that prompt the reader to reflect on their own situation

After this sweep: re-check Sweeps 1–5.

---

### Sweep 7: Zero Friction

**Have we removed every barrier between reading and acting?**

Look for:
- CTA asking for commitment the copy hasn't earned
- Objections raised but not addressed
- Unclear next steps ("Contact us" — for what? How long does it take?)
- Hidden costs or surprises implied
- Fine print that creates doubt

Risk reducers to add or flag as missing:
- "No credit card required"
- "Cancel anytime"
- Money-back guarantee
- Social proof immediately before the CTA
- Exact next-step description: "You'll get a 15-minute call with a founder"

Final check after all sweeps: run Sweeps 1–6 one more time.

---

## Word-Level Cuts

**Always cut:**
- Very, really, extremely, incredibly (weak intensifiers)
- Just, actually, basically, essentially (filler)
- "In order to" → "to"
- "That" (often unnecessary)
- Things, stuff (vague nouns)

**Replace:**

| Weak | Strong |
|------|--------|
| Utilize | Use |
| Implement | Set up |
| Leverage | Use |
| Facilitate | Help |
| Innovative | New |
| Robust | Strong |
| Seamless | Smooth |
| Cutting-edge | Modern |
| Elevate | Improve |

---

## Sentence Rules

- One idea per sentence
- Vary length: mix short punchy sentences with longer ones
- Front-load the important information
- Max ~25 words per sentence as a general guide
- Active voice: "We generate the report" not "The report is generated"

---

## Output Format

When editing, provide:

1. **Diagnosis** — what's wrong and where, before touching anything
2. **Edited copy** — the improved version in full
3. **Change log** — a brief list of what changed and why (especially for cuts and rewrites)
4. **Flags** — anything you couldn't fix because you need information (missing proof, unverifiable claims, unclear intent)
