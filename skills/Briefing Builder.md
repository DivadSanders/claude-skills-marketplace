---
name: Briefing Builder
description: >
  Runs a guided interview to build a personalized news intelligence prompt —
  ready to paste into a Cowork Scheduled Task or Claude Code Routine so it
  runs on a schedule without you having to think about it again.
  Use this skill when the user wants to set up a recurring news briefing,
  create a custom intelligence prompt, track specific industries or topics on a schedule,
  asks "build me a news briefing prompt", "set up my morning brief",
  "I want to track [topic] automatically", "create an intelligence prompt for me",
  "help me build a research routine", or "I want a daily digest of [topic]."
  Also trigger when the user mentions Cowork Scheduled Tasks, Claude Code Routines,
  or wants a prompt they can drop into a recurring task runner.
  Run this skill with Opus for best results — the interview and pillar design
  benefit from the stronger reasoning model.
category: productivity
tags: [news, briefing, intelligence, research, automation, Cowork, Claude-Code, scheduled-tasks, prompt-builder]
version: 1.0.0
author: DivadSanders
---

# Briefing Builder

> A 13-question interview. A master prompt. Drop it into Cowork or Claude Code and it runs itself.

## What This Does

Runs a structured interview that captures everything a good briefing prompt needs: your role, your focus areas, what to track, what to exclude, your sources, your geography, your format, and your schedule. It clusters your answers into logical topic pillars, shows you a sample story entry to confirm the format, and outputs a complete master prompt in a single code block — ready to paste into a Cowork Scheduled Task or Claude Code Routine.

When your priorities shift, run it again. Same interview, fresh prompt.

## When to Use

- You want a recurring news briefing but don't want to write the prompt yourself
- You're setting up a Cowork Scheduled Task or Claude Code Routine and need the prompt
- Your focus areas have shifted and your current briefing is stale
- You want something more specific than a general news summary — tailored to your role, your industry, your sources

## Example Prompts

- "Build me a news briefing prompt"
- "Set up my morning brief"
- "I want to track AI and fintech news automatically — help me build the prompt"
- "Create an intelligence prompt I can drop into Cowork"
- "I want a daily digest of what's happening in climate tech"

## Tip

Run this skill with **Opus** — the pillar design and story-type generation steps benefit from stronger reasoning. Switch back to your usual model once you have the master prompt.

---

## How to Deploy the Output

Once the interview is complete, you'll receive a master prompt in a code block. Two ways to run it on a schedule:

**Cowork Scheduled Tasks** (requires Pro or Max plan, desktop app open)
Cowork → Scheduled Tasks → New Task → paste the prompt → set your schedule.

**Claude Code Routines** (runs in the cloud — no laptop required)
Claude Code → Routines → New Routine → Remote → paste the prompt → set your schedule.

Either path turns a one-time prompt into a briefing that arrives on its own.

---

## The Interview

Ask questions one at a time, in order. Wait for each answer before continuing. Do not batch questions.

---

### Phase 1: Intake

**Q1 — Your role**
Tell me a bit about yourself. A few words on your role, what you do, and what you'll use this briefing for.

*Examples:*
- "VC investor at a Series A fund, focused on enterprise AI deals."
- "Marketing lead at a fintech startup, want to track competitor moves."
- "Independent researcher following climate policy and carbon markets."

---

**Q2 — Focus areas**
What industries or themes should this track?

*Examples: AI, FinTech, Climate, Defense, VC, Health Tech, Consumer, Real Estate*

---

**Q3 — Specific topics**
Within those areas, which topics matter most?

*Example: "Within AI: agentic workflows, enterprise adoption. Within FinTech: cross-border payments, embedded finance."*

---

**Q4 — Geography**
Any regions to prioritize? List them with an approximate coverage split, or say "global."

*Example: "30% Middle East, 20% Southeast Asia, rest global."*

---

**Q5 — Preferred sources**
Specific publications, newsletters, or firms to prioritize? Or say "auto-select."

---

**Q6 — Keywords**
Any companies, people, or regulatory terms to always flag? Or say "none."

---

**Q7 — Story count**
How many stories per briefing? (Suggested: 10–25)

---

**Q8 — News freshness**
How old can a story be?

a) 24–48 hours
b) 7 days
c) 14 days
d) 1 month

---

**Q9 — Frequency**
How often should this run?

a) Daily — specify time + timezone
b) Weekdays only — specify time + timezone
c) Weekly — specify day, time + timezone
d) On-demand only

---

**Q10 — Format**
How should each story be written?

a) Ultra-brief — 1-sentence headline + link
b) Quick brief — 2–3 sentences: what happened and why it matters
c) Analytical summary — 4–5 sentences with context, definitions, and impact
d) Narrative — flowing prose paragraph, no bullets

---

**Q11 — Anything else?**
Anything about your research preferences not covered yet — framings to avoid, story types you always want included or excluded, tone preferences, audience-specific context. Or say "nothing else."

---

**Q12 — Story types**
*Before asking this question:* generate 6–8 story-type categories most relevant to this user based on their answers to Q1 (role), Q2 (focus areas), and Q3 (specific topics). Categories should genuinely fit their domain — not a generic template.

A climate analyst might need "policy commitments," "carbon market shifts," or "extreme weather events." A consumer researcher might need "trend reports," "viral cultural moments," or "behavior shifts." Generate what fits.

The list below is reference only — use it for inspiration where relevant, ignore it where the user's domain calls for something different:
- Funding rounds, M&A, IPOs
- Product launches, feature releases
- Regulatory and policy shifts
- Leadership moves, hiring trends
- Research papers, benchmarks, technical breakthroughs
- Market data, earnings, financial results
- Strategic moves, partnerships, deals
- Opinion, analysis, contrarian takes

Present the tailored 6–8 categories and ask:

"Which 3–4 of these matter most? Rank them or describe a preferred mix — e.g. '40% funding, 30% product, 20% regulatory, 10% opinion'."

---

**Q13 — Exclusions**
Anything to systematically exclude? Companies, topics, story types, thresholds (e.g. funding rounds under $10M), framings, or coverage angles you don't want to see. Or say "none."

---

### Phase 2: Pillar Design

Using all answers above:

1. Propose 2–4 pillars — logical topic groupings based on the user's focus areas and story-type mix
2. For each pillar: name, what it covers, recommended story count
3. Briefly explain the clustering logic
4. Ask: "Does this structure work, or would you like to adjust groupings or story counts?"

Wait for confirmation before continuing.

---

### Phase 3: Format Preview

Show one sample story entry using the format chosen in Q10.

Ask: "Does this look right? Any changes before I generate the prompt?"

Wait for confirmation.

*Skip this phase if Q10 answer was (a) ultra-brief or (b) quick brief.*

---

### Phase 4: Summary Review

Present a clean summary:

- Reader profile (Q1)
- Focus areas and specific topics
- Pillars with story counts
- Geography, sources, keywords
- Total story count, freshness window, schedule, format
- Story type mix (Q12)
- Exclusions (Q13)
- Custom preferences (Q11)

Ask: "Does everything look correct? Confirm and I'll generate your master prompt."

Wait for explicit confirmation before Phase 5.

---

### Phase 5: Output

Once confirmed, respond with exactly:

"Here is your master prompt:"

Then output the complete prompt below in a single code block. No explanation or commentary after the code block.

---

```
[SCHEDULE: {Q9}]

# TASK: {title suited to reader profile} Intelligence Briefing

You are a strategic research analyst delivering a high-signal briefing of
{story count} stories for the following reader:

**READER PROFILE:** {Q1}

Calibrate topic selection, framing, and depth to this reader.

## STEP 1: RESEARCH FRAMEWORK

Scan for {story count} developments from the last {freshness window}.
Always flag content matching these keywords: {Q6}.

{For each pillar:}
**PILLAR [N]: [NAME] (Target: [X] stories)**
- Look for: [topics]
- Geographic priority: [geography]

**TARGET SOURCES:** {Q5}

**STORY TYPE MIX:** {Q12}
Weight the briefing toward these story types in the proportions specified.
Drop or down-rank stories that do not fit this mix.

**EXCLUSIONS:** {Q13}
Filter out anything matching these criteria before considering it for the
briefing. Apply at the research stage, not at the write-up stage.
If Q13 is "none," ignore this section.

**ADDITIONAL PREFERENCES:** {Q11}
Apply these preferences across research, writing, and delivery.
If Q11 is "nothing else," ignore this section.

## STEP 2: QUALITY VERIFICATION

1. Trace every story to its PRIMARY source (press release, filing, official
   dispatch, earnings release).
2. Original publication date MUST fall within the last {freshness window}.
   Exclude all secondary or retrospective coverage.
3. Strip all marketing language and PR framing.

## STEP 3: WRITING STYLE

{If Q10 = ultra-brief:}
Write each story as a single declarative sentence followed by the source link.
No additional context.

{If Q10 = quick brief:}
Write 2-3 sentences per story. Cover what happened and why it matters.
Plain and factual.

{If Q10 = analytical summary:}
Write 4-5 sentences per story. Cover what happened, define any technical or
financial terms in plain English, and explain the systemic or market impact.

{If Q10 = narrative:}
Write a short flowing paragraph per story. No bullets. Write as if explaining
to an intelligent friend who is not an expert in the field.

Across all formats:
- Spell out all acronyms and organization names on first use.
- Short, declarative sentences. Dense with facts, light on words.
- No em dashes, no semicolons. Periods and commas only.

## STEP 4: DELIVERY

Output the briefing directly in chat using this structure:

🚨 *[BRIEFING TITLE]* 🚨

{For each pillar:}
*[EMOJI] [PILLAR NAME] ([X] Stories)*

1. *[Headline]*
   - *Brief*: [story written per Step 3 format]
   - *Source*: [URL]

(Repeat for all stories)
```

---

## Completion Checklist

- [ ] All 13 questions answered before moving to Phase 2
- [ ] Questions asked one at a time — no batching
- [ ] Story-type categories in Q12 generated fresh from the user's profile — not pulled from the reference list
- [ ] Pillars confirmed by user before Phase 3
- [ ] Format preview shown and confirmed (skip if ultra-brief or quick brief)
- [ ] Summary review confirmed before generating output
- [ ] Master prompt output in a single code block with no commentary after it
- [ ] Deployment path explained (Cowork or Claude Code Routines)
