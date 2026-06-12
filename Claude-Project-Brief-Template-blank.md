# Claude Project Brief: Universal Template (Blank)

> This is the blank template. It contains the structure and guidance hints only, with no worked examples.
> For worked examples showing each section fully populated, use `Claude-Project-Brief-Template-with-examples.md` from the same repository.

---

<!--   COPY START: Copy everything between these markers into    -->
<!--   your own file named:                                      -->
<!--   "Claude Project Brief.md" or                             -->
<!--   "[Your Project Name] Claude Project Brief.md"            -->
<!--=============================================================-->

---

## Section 1: Document Header Block

> **What goes here:** The frontmatter block at the very top of your Brief. Claude uses the description field to decide when to load this document. Write it to trigger on any mention of your project name, technology stack components, or key feature terms. Be generous. It is better to trigger too often than to miss a session where the rules were needed.

```
---
name: [your-project-slug]
description: Non-negotiable rules, session discipline, and conventions
for [Your Project Name]. ALWAYS read this Brief at the start of any
session: writing code, running SQL, editing configuration, deploying,
or answering architecture questions. Mandatory if the user mentions
any of: [list your key tech terms, feature names, server names, file names].
---
```

---

## Section 2: Opening Statement

> **What goes here:** Two or three sentences establishing what this file is and why it exists. Include the phrase: every rule here exists because its violation caused a real failure. This tells Claude these rules are not preferences. They are lessons learned from real mistakes.

```markdown
# [Your Project Name]: Claude Project Brief

This document is the authoritative source of non-negotiable rules for
all [Your Project Name] development work. It is not a reference
document. It is a project rules document. Every rule here exists
because its violation caused a real failure in a real session.
```

---

## Section 3: Authority Hierarchy

> **What goes here:** A three-layer hierarchy telling Claude how to resolve conflicts between what it sees in the live session, what this file says, and any background memories it holds. This prevents Claude from overriding hard-won rules because something appeared to work differently today.

```markdown
**Authority hierarchy: three layers**

**Layer 1: Live conversation context.**
Whatever is discovered, fixed, or decided within the current session
thread is the ground truth for that session. No document overrides
direct evidence from the running system.

**Layer 2: This Claude Project Brief.**
Two types of rules live here:
- Structural rules: environment constraints that never change
  regardless of session outcomes [give examples: server access method,
  file transfer method, approved terminal commands]. These cannot be
  overridden by Layer 1 even if something appears to work without
  following them.
- Architectural state rules: current state of the codebase [give
  examples: column names, file paths, service names, approved
  vocabulary]. A deliberate architectural change in a live session
  supersedes these. That is also the moment this Brief must be updated
  at session close.

**Layer 3: Background context and project memory.**
Useful supporting context: background, preferences, session patterns.
Where it conflicts with this Brief, treat it as a signal that the
Brief may need updating rather than that the background context is
authoritative.
```

---

## Section 4: How to Find Authoritative Documents

> **What goes here:** A short guide telling Claude where to find definitive project documents. Key principle: always use the highest version number. Never assume a version from memory.

```markdown
## How to Find Authoritative Documents

Search project knowledge for [DocumentNamePattern] and use the result
with the highest version number. Never hardcode a version. Never
assume a version from memory.

- [Area 1] guide: search [Pattern], use highest version
- [Area 2] guide: search [Pattern], use highest version
```

---

## Section 5: Session Open Discipline

> **What goes here:** Mandatory steps Claude must complete at the start of every session, before any code or commands are produced.
>
> **Why the self-refinement check matters: context rot.**
> As a chat thread grows longer, Claude's recall of earlier instructions degrades. This is known as context rot. Claude's context window processes everything in one shared buffer. Your messages, replies, uploaded files, and the Project Brief all compete for the same space. Performance follows a U-shaped curve: best recall at the very beginning and end, worst recall in the middle. As a thread grows, your Brief drifts toward that dead zone.
>
> The fix takes seconds. At the start of every session, instruct Claude to confirm it has read and is actively applying the Brief. If a thread has grown long, instruct Claude to re-read the Brief before continuing.

```markdown
## Session Open Discipline: Mandatory Before Any Work

1. Confirm you have read and are actively applying the Claude Project
   Brief for this project. If this thread is long or context feels
   thin, re-read the Brief now and confirm which version you are
   working from before proceeding.
2. Confirm the session number or reference. Ask if not clear.
3. Confirm all documents from the previous session have been uploaded
   or committed. Do not proceed until confirmed.
4. [Take a snapshot / create a backup / confirm Git branch state]
5. If any design questions are unresolved, resolve them fully before
   writing any code.
```

---

## Section 6: Session Close Gate

> **What goes here:** A sequential checklist completed before declaring a session closed. This is the most important section. It prevents knowledge from living only in a chat thread and disappearing. Work through every step in order.

```markdown
## Session Close Gate: Complete in Order Before Closing

**Step 1: Snapshot, backup, or commit**
[Describe the save-state action for your environment.]

**Step 2: Updated documentation**
Updated guide produced for every area touched this session.
Version number incremented.

**Step 3: Handover note covering:**
- Summary of what was done
- Current state of every in-progress item
- Lessons learnt, including any new rules discovered this session
- Next session priority list
- Footer: "Upload or commit before opening next session"

**Step 4: Backlog or ticket tracker updated**
New items added. Status changes recorded. Decisions logged.

**Step 5: Claude Project Brief updated if required**
If any new non-negotiable rule was discovered this session, add it
here before closing. One rule, one entry.

**Step 6: Thread sweep**
Read back through the session. Is there any decision, discovery, or
constraint that exists only in this conversation and has not been
captured in a document? If yes, capture it before closing.

**Step 7: Upload or commit**
All produced documents uploaded or committed. Confirm before closing.
```

---

## Section 7: Non-Negotiable Rules

> **What goes here:** The core of the document. Each rule is a specific, testable constraint grouped by category. Each rule has a unique code (e.g. T-01, P-01) so it can be referenced without ambiguity, a short bold title, and one or two sentences of explanation.
>
> Rules are discovered, not invented. Add a rule only when breaking it caused a real failure. Start with a small number of real rules. Your first version may have 10. That is correct.

---

### Category T: Terminal and Server Access Rules

> **What goes here:** How to connect to and operate on your servers. Cover: which user to run commands as, approved connection methods, how not to write files to the server.

```markdown
**Rule T-01: [Title]**
[State the rule positively and negatively. Always do X. Never do Y.]

**Rule T-02: [Title]**
[Rule text.]
```

---

### Category P: Database Rules

> **What goes here:** Rules for your database. Cover: which user to connect as, which database to use per environment, how to safely run schema changes.

```markdown
**Rule P-01: [Title]**
[Rule text.]

**Rule P-02: [Title]**
[Rule text.]
```

---

### Category F: File Transfer Rules

> **What goes here:** How files move between your local machine and the server. Cover: approved transfer method, what to verify after transfer.

```markdown
**Rule F-01: [Title]**
[Rule text.]
```

---

### Category A: Application and Framework Rules

> **What goes here:** Rules specific to your framework or runtime. Cover: caching behaviour, build commands, environment variable management, third-party library quirks discovered in practice.

```markdown
**Rule A-01: [Title]**
[Rule text.]
```

---

### Category D: Diagnostic Rules

> **What goes here:** How to investigate problems. The most important rule is always: diagnose completely before producing any fix.

```markdown
**Rule D-01: Diagnose completely before producing any fix**
[Expand on this for your environment.]
```

---

### Category G: Governance Rules

> **What goes here:** How decisions are made and recorded. Cover: approval process for removals, documentation standards, output format defaults.

```markdown
**Rule G-01: Code must only ADD features without explicit approval to remove**
[Expand on your team's approval process.]

**Rule G-02: Default output format is [Markdown / Word / etc.]**
[State your team's standard.]
```

---

## Section 8: Self-Validation Checklist

> **What goes here:** A table of checks Claude runs through internally before producing any output. Claude must not produce code, SQL, or terminal commands until all applicable checks pass. Map each check directly to a rule above.

```markdown
## Self-Validation Checklist

Before producing any output run through this checklist internally.
Do not skip steps.

| # | Check | Applies when |
|---|---|---|
| 1 | Claude Project Brief read and actively applied? | Every session |
| 2 | Session reference confirmed and previous documents committed? | Session open |
| 3 | Safety snapshot, backup, or branch check completed? | Session open |
| 4 | Authoritative document retrieved at highest version? | Any documented area |
| 5 | Schema check run before any SQL? | Any SQL |
| 6 | File transfer method confirmed? | Any file transfer |
| 7 | [Framework-specific check, e.g. config cache cleared?] | [Relevant trigger] |
| 8 | Design questions fully resolved before first line of code? | Any build session |
| [Add a row for every significant rule in your project] | | |
```

---

## Section 9: Version History

> **What goes here:** A table tracking changes to this Brief. Every time a new rule is added because a violation caused a real failure, log it here. This gives future colleagues context for why each rule exists.

```markdown
## Version History

| Version | Date | Change |
|---|---|---|
| 1.0 | [YYYY-MM-DD] | Initial: rules established at project start |
| 1.1 | [YYYY-MM-DD] | Added [Rule X] after [what went wrong] |
```

---

## Section 10: Footer

> **What goes here:** A brief footer stating this document's authority and maintenance instruction. Keep it short.

```markdown
---
*This document is the authoritative rules register for [Your Project Name].*
*Authority hierarchy: live session context, then this Brief, then background context.*
*When a new non-negotiable rule is discovered, add it before the session closes.*
```

---

<!--=============================================================-->
<!--   COPY END                                                   -->
<!-

---

*Claude-Project-Brief-Template-blank. Built from a real production project, validated across multiple independent projects. Freely adaptable for any project. British English throughout.*
