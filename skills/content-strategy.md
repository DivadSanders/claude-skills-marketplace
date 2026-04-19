---
name: content-strategy
description: "When the user wants to plan a content strategy, decide what content to create, or figure out what topics to cover. Also use when the user mentions 'content strategy,' 'what should I write about,' 'content ideas,' 'blog strategy,' 'topic clusters,' 'content planning,' 'editorial calendar,' 'content marketing,' 'content roadmap,' 'what content should I create,' 'blog topics,' 'content pillars,' or 'I don't know what to write.'"
category: writing
tags: [content-strategy, SEO, blog, content-marketing, SaaS, topic-clusters, editorial]
version: 2.0.0
author: DivadSanders
---

# Content Strategy

> Plan content that gets found, gets shared, and builds authority — not content that disappears into the void.

## What This Does

Gives Claude a systematic framework for planning content that actually works. Instead of generic "write about X" advice, it produces a prioritized content plan grounded in customer research, search behavior, and your product's positioning.

## When to Use

- You don't know what to write about
- You're writing content but nothing is getting traction
- You want to build a content strategy from scratch
- You need to prioritize a backlog of content ideas

## Example Prompts

- "I run a B2B SaaS for construction project managers. Help me build a content strategy"
- "Here are 50 keyword ideas from Ahrefs — help me turn this into a prioritized content plan"
- "What topics should I own as a founder building in the dev tools space?"

---

## The Core Principle

Every piece of content must be **searchable**, **shareable**, or both. Prioritize in that order. Search traffic is the foundation.

**Searchable content** captures existing demand. People are already looking for it.  
**Shareable content** creates demand. It spreads ideas and gets people talking.

If content is neither searchable nor shareable, don't make it.

---

## Before Planning

Gather this context. If the user hasn't provided it, ask before building a strategy:

**Business context**
- What does the company do? What problem does it solve?
- Who is the ideal customer? (role, company size, industry)
- What's the goal for content? (organic traffic, leads, authority, all three)

**Customer intelligence**
- What questions do customers ask before buying?
- What objections come up in sales calls?
- What language do customers use to describe their problem?
- What keeps them up at night?

**Current state**
- Do you have existing content? What's getting traction?
- What can you realistically produce? (articles per month, any video/audio capacity)

**Competitive landscape**
- Who are main competitors?
- What content are they ranking for?
- Where are the gaps?

---

## Searchable Content

### Use-Case Content
Formula: `[persona] + [use case]` — targets long-tail keywords with high intent.
- "Project management for architects"
- "Invoice tracking for freelance designers"
- "Time tracking for remote dev teams"

### Hub and Spoke
Hub = comprehensive overview. Spokes = related subtopics. All interlinked.

```
/blog/topic-hub
├── /blog/topic-subtopic-1
├── /blog/topic-subtopic-2
└── /blog/topic-subtopic-3
```

Build the hub first, then spokes. Don't build spokes into a void.

**Note:** Most blogs work fine with `/blog/post-title`. Only build dedicated hub pages for topics with genuine depth — multiple layers of subtopics, significant search volume, and a long-term authority play.

### Template and Resource Content
High search intent + product adoption = strong combo.
- Target: "[task] template," "[workflow] checklist," "[process] spreadsheet"
- Provide standalone value
- Show how your product enhances it

---

## Shareable Content

### Thought Leadership
Name something people feel but haven't articulated. Challenge conventional wisdom with evidence. Be specific — "5 things about X" is not thought leadership.

### Original Data
- Analyze your own product usage data (anonymized)
- Pull and interpret public datasets
- Run a simple experiment and publish the result

### Case Studies
Structure: Challenge → Solution → Specific Results → Key Learnings

Numbers matter. "Reduced time by 40%" beats "saved significant time."

### Contrarian Takes
The strongest shareable content disagrees with something the audience currently believes. Earn the right to disagree by showing your work.

---

## Content by Buyer Stage

### Awareness ("I have a problem")
Modifiers: "what is," "how to," "guide to," "why does"

Example: If customers struggle with cash flow:
- "What is cash flow forecasting"
- "How to read a cash flow statement"
- "Guide to 13-week cash flow"

### Consideration ("I'm evaluating options")
Modifiers: "best," "top," "vs," "alternatives," "comparison"

Example:
- "Best cash flow tools for small businesses"
- "Float vs Pulse vs Fathom"
- "Xero alternatives for cash flow"

### Decision ("I'm ready to choose")
Modifiers: "pricing," "reviews," "demo," "free trial"

Example:
- "Float pricing — is it worth it?"
- "[Product] reviews"
- "How to set up [Product]"

### Implementation ("I chose, now I need help")
Modifiers: "templates," "tutorial," "how to use," "setup guide"

These are often underrated. Customers who find implementation content convert and retain better.

---

## Content Pillars

Pillars are the 3–5 core topics your brand will own. Every piece of content maps to a pillar.

**How to pick pillars:**
1. What problems does your product solve? (Product-led)
2. What does your ICP need to learn to be successful? (Audience-led)
3. What has search volume in your market? (Search-led)
4. What are competitors not covering well? (Gap-led)

**Criteria for a good pillar:**
- Directly connected to your product's value
- Broad enough for 10+ subtopics
- Your team has genuine insight on it
- There's an audience actively looking for it

---

## Prioritization Framework

Score content ideas on four factors:

| Factor | Weight | Questions to ask |
|--------|--------|-----------------|
| Customer relevance | 40% | How often does this come up? How painful is it? |
| Content-market fit | 30% | Can you offer unique insight? Does it lead to product interest? |
| Search potential | 20% | What's the volume? How competitive? Growing or declining? |
| Resources required | 10% | Do you have the expertise? What assets do you need? |

Score each 1–10, apply weights, rank by total. Build the top items first.

---

## Mining Content Ideas

**From keyword data (Ahrefs, SEMrush, GSC exports):**
Group by topic cluster → map to buyer stage → identify quick wins (decent volume, low competition, high relevance) → flag gaps where competitors rank but you don't.

**From customer conversations:**
Questions asked = FAQ or how-to content. Pain points = problem-framing articles. Objections = content that addresses hesitation before it comes up in sales. The exact phrases they use = your copy vocabulary.

**From competitor analysis:**
`site:competitor.com/blog` — find their top-performing posts, identify what they cover repeatedly, spot what they haven't touched, look for outdated content you can improve.

**From forums:**
`site:reddit.com/r/[subreddit] [topic]` — look for upvoted questions, repeating frustrations, and answers that people find valuable.

---

## Output Format

When delivering a content strategy, provide:

**1. Content Pillars**
3–5 pillars with rationale for each, subtopic clusters, and connection to product value.

**2. Priority Content List**
For each recommended piece: title, searchable/shareable/both, content type, target keyword, buyer stage, and one-line rationale.

**3. Topic Cluster Map**
How content interconnects — which pieces support which hub, what internal linking makes sense.

**4. Quick Wins**
3–5 pieces to start immediately based on low competition + high relevance.
