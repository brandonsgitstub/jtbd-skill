# JTBD Interview Guide — Claude Skill

A Claude skill for running Jobs-to-be-Done research. Give it context about what you're exploring and it generates a complete, ready-to-run interview guide. Paste in your notes after the interviews and it synthesizes them into job statements, opportunity areas, and strategic recommendations — all as a formatted `.docx`.

---

## What It Does

This skill has two modes:

**→ Guide mode** — You're planning interviews and need a discussion guide.
Give Claude the product area, target user, and any hypotheses you're testing. It generates a structured guide with screener criteria, warm-up questions, a hiring trigger sequence, and a progress/struggle sequence. The output includes interviewer notes throughout (which questions to skip, where to pause, what each section is trying to accomplish).

**→ Synthesis mode** — You've run interviews and need to make sense of them.
Paste in raw notes, transcripts, or a filled per-interview template. Claude extracts hiring triggers, functional/emotional/social jobs, workarounds, and switch moments — then writes a synthesis doc with job statements, cross-interview themes, a struggle map, and opportunity areas.

---

## How to Use It

### 1. Add the skill to Claude

Upload `SKILL.md` to your Claude project. The skill auto-detects which mode you need based on your message.

### 2. Guide mode — what to tell Claude

Provide at minimum:
- **Product area or initiative** — what is the research for?
- **Target user** — role, company type, or segment
- **Any hypotheses** — what do you already believe? (optional but useful)

**Example prompt:**
```
I'm running discovery on our onboarding flow for early-stage startup PMs. 
I want to understand why some users get to their "aha moment" in week one 
while others churn. Can you build me a JTBD interview guide?
```

**What you get:**
- A Screener with 4–6 criteria to find participants who've recently made a meaningful decision in the space
- A Warm-up section (3–4 questions) to build rapport and prime episodic memory
- A Hiring Trigger sequence (15–20 min) anchored to a specific past event — not hypotheticals
- A Progress & Struggle sequence (15–20 min) mapping what users were trying to accomplish and where they got stuck
- Interviewer notes throughout: what to skip, where to pause, what each section is trying to surface
- A one-page Interviewer Briefing at the front of the doc

---

### 3. Synthesis mode — what to provide

Paste in notes from **2+ interviews**. Accepted formats:
- Raw notes or transcripts
- A filled per-interview template (the skill can provide this template if you ask)
- A mix of both

**Example prompt:**
```
I ran 4 interviews with mid-market RevOps leads about our reporting module. 
Here are my notes: [paste notes]
```

**What you get:**
- **Job statements** (2–5) written in standard format: *"When [situation], I want to [motivation], so I can [expected outcome]."*
- **Key themes** (3–6) — cross-interview patterns, each with an anonymized quote
- **Struggle map** — where in the progress journey users consistently get stuck, organized by stage (not by feature)
- **Opportunity areas** (2–4) written as: *"Help [persona] [do job] without [current struggle]."*
- **What we didn't hear** — notable absences: jobs or struggles you expected but didn't find
- **Recommended next steps** — 2–3 concrete actions

---

## Example Output

### Guide mode output (excerpt)

> **Section 3 — Hiring Trigger Sequence**
> *Purpose: Identify the specific moment this person decided to look for a new or better solution. This is the most important data in the interview — spend time here.*
>
> - "Take me back to when you first started looking for a different way to handle [workflow]. What was going on at the time?"
> - "What specifically happened that made you think the current approach wasn't working?"
> - "Was there a particular moment — or did it build up over time?"
> - "Who else was involved in that decision?" `[pause — let them think]`
> - "What would have had to be true for you to stick with what you had?" `[skip if short on time]`

---

### Synthesis mode output (excerpt)

> **Job Statement 1**
> When presenting pipeline data to my VP in a weekly review, I want to pull a clean, up-to-date snapshot without manually reconciling three sources, so I can spend the meeting discussing strategy instead of defending the numbers.
>
> **Struggle Map — Reporting Stage**
> Users consistently stall at the "assembly" stage: they know what they want to show but can't get the data into a single place cleanly. Workarounds include maintaining a separate Google Sheet that acts as a manual join layer — which 3 of 4 participants described independently.
>
> **Opportunity Area 2**
> Help RevOps leads create board-ready pipeline snapshots without reconciling data from CRM, spreadsheet, and BI tool each time.

---

## File Structure

```
jtbd-interview-guide/
├── SKILL.md                        # The Claude skill — upload this to your project
└── references/
    ├── jtbd-primer.md              # Core JTBD concepts adapted for SaaS PM practice
    ├── screener-templates.md       # Screener criteria patterns by research context
    ├── question-sequences.md       # Full question bank: hiring trigger, progress, struggle
    ├── synthesis-template.md       # Per-interview fill-in template
    └── synthesis-format.md         # Synthesis doc structure with quality standards
```

---

## Design Notes

This skill uses flexible JTBD principles adapted for modern SaaS PM practice — not strict Christensen/Ulwick orthodoxy. The core insight driving the question design: **anchor to specific past events, not hypotheticals**. "Tell me about the last time you..." surfaces real hiring triggers. "What would you typically do when..." surfaces rationalizations.

The synthesis output is structured to be stakeholder-ready. Job statements and opportunity areas are written in formats you can drop directly into a PRD or roadmap review.
