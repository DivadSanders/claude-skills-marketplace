---
name: Inbox Triage
description: >
  Gmail inbox triage skill. Reads your Gmail inbox for a specified time window,
  filters for emails that need a response or decision, and outputs a structured
  action-items list with sender, subject, what they actually need, urgency level,
  and a one-line draft opener for each.
  Requires the Gmail connector to be active.
  Trigger when the user says "/emails-tasks", "/inbox", "triage my inbox",
  "what needs my attention in Gmail", "check my emails", "what do I need to respond to",
  "any urgent emails", or any variation of wanting to know what action items are
  waiting in their inbox. Also trigger when the user specifies a time window like
  "/emails-tasks 4h", "check the last 2 hours", or "what came in this morning."
  Default time window if none is specified: 8 hours.
category: productivity
tags: [gmail, email, inbox, triage, action-items, productivity, mobile]
version: 1.0.0
author: DivadSanders
---

# Inbox Triage

> Type `/emails-tasks`. See only what needs you. Skip everything that doesn't.

## What This Does

Reads your Gmail inbox for a set time window, throws out everything that doesn't require your attention (receipts, notifications, newsletters, automated emails), and surfaces only what needs a reply or a decision. For each email that qualifies: who it's from, what they actually need, how urgent it is, and a one-line opener so you can start the reply immediately.

No preamble. No summary of what was filtered. Just the action items, and one line at the end telling you how many there are.

Works from any device — including from your phone via Dispatch.

## When to Use

- You want a fast scan of what needs your attention without opening your inbox
- You've been away for a few hours and want to catch up without reading everything
- You're on your phone and need to triage quickly
- You want to start your day knowing exactly what requires a reply before you open a single thread

## Example Prompts

- `/emails-tasks` — triages the last 8 hours
- `/emails-tasks 4h` — triages the last 4 hours
- `/emails-tasks 2h` — triages the last 2 hours
- "Check my inbox for anything urgent"
- "What do I need to respond to from this morning?"

## Requirements

The **Gmail connector** must be active. If Gmail isn't connected, this skill cannot run — connect it via Settings → Connectors before invoking.

---

## How It Works

### Step 1 — Set the Time Window

The user will typically say `/emails-tasks` or `/emails-tasks [time window]`.

- If a time window is specified (e.g., `4h`, `2h`, `30m`), use that.
- If no time window is specified, default to **8 hours**.

---

### Step 2 — Read the Inbox

Use the Gmail tool to fetch all emails received within the specified window. Cast a wide net — include threads, not just new emails.

---

### Step 3 — Classify Each Email

For each email, assign one category:

| Category | Criteria |
|---|---|
| **Response needed** | A real person is waiting for a reply |
| **Decision needed** | Requires judgment or approval — may not need a written reply |
| **No action** | FYI, receipts, notifications, marketing, automated emails |

**Filter rule:** Only surface Response needed and Decision needed. No action emails are noise — skip them entirely.

**Classify based on what the sender actually needs, not just what the email contains.** A calendar invite from a colleague is a Decision. A newsletter from someone you follow is No action — even if it's interesting. An automated Stripe receipt is No action. A teammate asking if you saw their PR is Response needed.

**One exception — Notable reads:** If a real human creator (someone you subscribe to, a collaborator, a person you follow) sent something substantive and directly relevant to your work — not a platform notification, not marketing — flag it separately in Step 4b. Never mix these with action items.

---

### Step 4 — Output the Action Items

For every email classified as Response needed or Decision needed, output one entry in this exact format:

---

**From:** [Sender name — company or context if relevant]
**Subject:** [Subject line]
**What they need:** [One sentence — the specific action required, not a description of the email]
**Urgency:** [Today / This week / No urgency]
**Draft opener:** [One sentence to start the reply]

---

**Quality rules:**

**What they need** — name the actual ask. "Approval on the revised contract before their Friday deadline" is correct. "They sent a contract" is not.

**Urgency** — assess from the *sender's* perspective, not just whether they stated a deadline. If someone is blocked waiting on you, that's Today even if they didn't say so. If a vendor is following up on an invoice due next week, that's This week.

**Draft opener** — this is the hardest part of any email: starting it. Write one sentence that sounds direct and human. Not "I hope this finds you well." Something like:
- "Thanks for flagging — here's where I land on this:"
- "Let's do it — I'll need X from your end first."
- "Looping in [name] who owns this — they'll take it from here."

---

### Step 4b — Notable Reads (Optional)

After the action items, scan for emails from real human creators — newsletter writers, collaborators, people you follow. These are not tasks. Surface them only if they're substantive and relevant to your work.

**Include if:**
- A real person (not a platform) published something directly relevant to what you're working on
- A collaborator sent something worth reading even though it doesn't require a reply

**Skip if:**
- Platform notifications (subscriber counts, payment confirmations, analytics digests)
- Pure marketing or promotional content
- Content with no clear connection to your work

If anything qualifies, output this section after the action items:

---

**Worth a look**

- **[Creator / Publication]** — "[Subject or description]" — one sentence on what it's about or why it's relevant.

---

Cap at 2–4 items. If nothing qualifies, omit this section entirely. Don't pad it.

---

### Step 5 — Summary Line

End with exactly one line:

**[N] items need your attention** — [response needed: X, decisions: Y]

If there were no action items but there was a Worth a look section:

**Inbox is clear** — nothing needs a reply, but a few things worth reading above.

That's it. No preamble. No explanation of the filtering process. No "here's what I found." Just the output.

---

## Output Quality Standards

| What to avoid | Why |
|---|---|
| Describing an email instead of naming the ask | "They sent a document" tells you nothing actionable |
| Marking everything as Today | Urgency loses meaning if everything has it |
| Generic draft openers ("I hope this finds you well") | If you wouldn't say it, don't write it |
| Including platform notifications in Notable reads | Automated emails are not creator content |
| Padding the Worth a look section | If nothing qualifies, say nothing |
| Explaining what you filtered and why | The user doesn't need a report — they need the output |

---

## Completion Checklist

- [ ] Gmail connector confirmed active
- [ ] Time window applied (explicit from user, or 8h default)
- [ ] All emails in window fetched, including threads
- [ ] Each email classified: Response needed / Decision needed / No action
- [ ] Action items output in correct format — one entry per email
- [ ] "What they need" names the specific ask, not a description
- [ ] Urgency assessed from sender's perspective, not just stated deadlines
- [ ] Draft opener sounds direct and human — not a template phrase
- [ ] Notable reads section included only if something genuinely qualifies (2–4 max)
- [ ] Summary line at end — one line only
- [ ] No preamble, no process explanation, no padding
