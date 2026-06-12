# Claude Project Brief: Universal Template v1.8

---

## READ THIS FIRST

**What is this file?**

A template for creating a Claude Project Brief, a project rules document that lives in your Claude.ai project knowledge area. Claude reads it at the start of every session and applies its rules automatically. Think of it as a standing instruction manual that travels with every conversation in your project.

**Two things to know before you start.**

**1. This template is specific to Claude.ai chat projects.** It works through the project knowledge area in Claude.ai. It is not designed for Claude Code, the Anthropic API, or third-party Claude integrations. If you are using Claude Code, look at the Karpathy CLAUDE.md convention instead.

**2. This template is particularly suited to vibe coding.** Vibe coding gets things built fast. You describe what you want, Claude builds it, you iterate, the project grows. The Claude Project Brief is what stops that speed from working against you as the project grows. It adds the session structure, failure memory, and context discipline that vibe coding is otherwise missing. If you are an experienced developer with established engineering practice already in place, this template still has value but you will need less of it.

**Where this template came from.**

It was built from a real production project developed across 70+ sessions on Claude.ai. The copy-and-paste notepad that preceded it was not unique to that project. Several other independent projects were running the same workaround in parallel. The template was tested against all of them. It worked across every one. Different projects, different tech stacks, same problem, same fix.

**How to use this file.**

**New project from scratch:** Work through each section below. The hints in blockquotes explain what to write. The EXAMPLE blocks show you a populated version using a fictitious web project called Birchwood Booking. Delete the hints and examples when your version is complete and upload the finished file to your Claude project knowledge area.

**Existing project with documents already in Claude:** Paste the opening prompt from the Quick-Start section at the end of this file. Claude will read your existing architecture docs, business requirements, product blueprint, and project memory and generate a part-filled Brief for you automatically. Review the output, correct anything that does not match reality, and add the rules only you know from experience.

**Keep it updated.** Every time a session uncovers a new rule, add it to the Brief before closing the session. A Brief that stops being updated stops being useful. This is not a one-time setup. It is a living document.

> **Note:** A blank version of this template (without the EXAMPLE blocks) is also available in this repository as `Claude Project Brief Template (blank).md`. Use the blank version once you understand the structure and want a clean starting point.

---

> **Duplication note for experienced users:** The Quick-Start Summary at the end of this file covers advantages, common objections, and the opening prompt. If you are already familiar with the concept and just want the template structure, everything between the COPY START and COPY END markers is what you need.

---

<!--=============================================================-->
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

> **EXAMPLE**
> ```
> ---
> name: birchwood-booking
> description: Non-negotiable rules, session discipline, and conventions
> for the Birchwood Booking web application. ALWAYS read this Brief at
> the start of any session: writing code, running migrations, editing
> config, or answering architecture questions. Mandatory if the user
> mentions: Birchwood, booking, Laravel, MySQL, Nginx, Blade, Tailwind,
> server, migration, seed, deploy.
> ---
> ```

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

> **EXAMPLE**
> ```markdown
> # Birchwood Booking: Claude Project Brief
>
> This document is the authoritative source of non-negotiable rules
> for all Birchwood Booking development work. It is not a reference
> document. It is a project rules document. Every rule here exists
> because its violation caused a real failure in a real session.
> ```

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

> **EXAMPLE**
>
> **Layer 1: Live conversation context.** Whatever is discovered in the current session is ground truth.
>
> **Layer 2: This Claude Project Brief.**
> - Structural rules: connect via SSH as deploy user, transfer files via SCP, never paste files into terminal.
> - Architectural state rules: current table names, column names, route prefixes. A deliberate change supersedes these. Update the Brief at session close.
>
> **Layer 3: Background context.** Where it conflicts with this Brief, update the Brief.

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

> **EXAMPLE**
>
> - Database migration guide: search `Birchwood-Migration-Guide`, use highest version
> - Deployment guide: search `Birchwood-Deploy-Guide`, use highest version
> - UI component library: search `Birchwood-UI-Spec`, use highest version

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

> **EXAMPLE**
>
> 1. Confirm you have read and are actively applying the Birchwood Booking Claude Project Brief. If this thread is long, re-read the Brief and confirm the version before proceeding.
> 2. Confirm the session reference. Ask if not clear.
> 3. Confirm previous session migration files and notes are committed to the `dev` branch.
> 4. Create a database backup before any schema changes: `mysqldump -u root -p birchwood_db > /var/backups/birchwood_pre_session.sql`
> 5. Confirm working branch is `dev`, not `main`. Never work directly on `main`.
> 6. Resolve any outstanding design questions before writing any code.

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

> **EXAMPLE**
>
> **Step 1: Commit** all changed files to `dev` branch with a descriptive message.
> **Step 2: Updated guides.** Update migration guide and deploy guide if any steps changed this session.
> **Step 3: Handover note** covering what was built, current state, lessons learnt, next priority list.
> **Step 4: GitHub Issues** updated with new or resolved items.
> **Step 5: Claude Project Brief updated** if any new rule was discovered.
> **Step 6: Thread sweep.** Anything discovered only in chat that has not been committed?
> **Step 7: Push** the `dev` branch and confirm it was accepted.

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

> **EXAMPLE**
>
> **Rule T-01: Always connect via SSH as the `deploy` user, never as `root`**
> The root account is locked for interactive sessions. Use `ssh deploy@birchwood.example.com`. If a command needs elevated privileges, use `sudo`.
>
> **Rule T-02: Never write files using `echo` one line at a time**
> Multi-line files written with repeated `echo >>` produce inconsistent line endings. Use `nano`, SCP, or SFTP instead.

---

### Category P: Database Rules

> **What goes here:** Rules for your database. Cover: which user to connect as, which database to use per environment, how to safely run schema changes.

```markdown
**Rule P-01: [Title]**
[Rule text.]

**Rule P-02: [Title]**
[Rule text.]
```

> **EXAMPLE**
>
> **Rule P-01: Always connect as `birchwood_app` for application queries, never as `root`**
> The root MySQL user has global privileges. Application queries always use `mysql -u birchwood_app -p birchwood_db`.
>
> **Rule P-02: Always `DESCRIBE tablename` before writing any query**
> Never assume column names from memory. One check before writing saves a failed query.
>
> **Rule P-03: Test migrations on `dev` database before running on `production`**
> Never run an untested migration on the production database.

---

### Category F: File Transfer Rules

> **What goes here:** How files move between your local machine and the server. Cover: approved transfer method, what to verify after transfer.

```markdown
**Rule F-01: [Title]**
[Rule text.]
```

> **EXAMPLE**
>
> **Rule F-01: Transfer all PHP, JS, and CSS files via SCP or SFTP only**
> Never paste file content directly into a terminal session. Use `scp localfile.php deploy@birchwood.example.com:/var/www/birchwood/`.
>
> **Rule F-02: Verify with `md5sum` on both sides after any file transfer**
> Confirm the transferred file is byte-identical to the source before restarting any service.

---

### Category A: Application and Framework Rules

> **What goes here:** Rules specific to your framework or runtime. Cover: caching behaviour, build commands, environment variable management, third-party library quirks discovered in practice.

```markdown
**Rule A-01: [Title]**
[Rule text.]
```

> **EXAMPLE**
>
> **Rule A-01: Always run `php artisan config:clear` after any `.env` change**
> Laravel caches the config. A changed value is not picked up until the cache is cleared.
>
> **Rule A-02: Never run `php artisan migrate` on the production server without a backup**
> Always complete Step 1 of Session Open Discipline before any migration on production.
>
> **Rule A-03: Named routes must be used in all Blade templates. Never hardcode URLs.**
> Hardcoded URLs break when the application is served from a subdirectory.

---

### Category D: Diagnostic Rules

> **What goes here:** How to investigate problems. The most important rule is always: diagnose completely before producing any fix.

```markdown
**Rule D-01: Diagnose completely before producing any fix**
[Expand on this for your environment.]
```

> **EXAMPLE**
>
> **Rule D-01: Diagnose completely before producing any fix**
> Never make one-fix-at-a-time passes without root cause analysis first. Read the Laravel log, identify the exact error, confirm the cause from evidence, then write the fix.
>
> **Rule D-02: Check the Nginx error log before assuming the application is at fault**
> A 502 Bad Gateway is Nginx failing to reach PHP-FPM, not an application error.

---

### Category G: Governance Rules

> **What goes here:** How decisions are made and recorded. Cover: approval process for removals, documentation standards, output format defaults.

```markdown
**Rule G-01: Code must only ADD features without explicit approval to remove**
[Expand on your team's approval process.]

**Rule G-02: Default output format is [Markdown / Word / etc.]**
[State your team's standard.]
```

> **EXAMPLE**
>
> **Rule G-01: No feature may be removed without a recorded team decision**
> All removals require a log entry with date, reason, and who approved.
>
> **Rule G-02: Default output format is Markdown `.md`**
> All session notes, guides, and handover documents are produced in Markdown unless explicitly requested otherwise.
>
> **Rule G-03: Any schema change requires a migration file. Never use a manual `ALTER TABLE`.**
> Direct schema changes cannot be tracked, replicated, or rolled back.

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

> **EXAMPLE**
>
> | # | Check | Applies when |
> |---|---|---|
> | 1 | Birchwood Booking Brief read and applied? | Every session |
> | 2 | Session reference confirmed and previous work committed? | Session open |
> | 3 | `mysqldump` backup completed? | Before any migration |
> | 4 | Working branch confirmed as `dev`, not `main`? | Session open |
> | 5 | `DESCRIBE tablename` run before any query? | Any SQL |
> | 6 | File transferred via SCP/SFTP? | Any file transfer |
> | 7 | `php artisan config:clear` run after any `.env` change? | Any config change |
> | 8 | Migration tested on `birchwood_dev` before production? | Any migration |
> | 9 | Named routes used, no hardcoded URLs? | Any frontend template |
> | 10 | Design questions resolved before writing code? | Any build session |

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

> **EXAMPLE**
>
> | Version | Date | Change |
> |---|---|---|
> | 1.0 | 2026-01-10 | Initial: rules established at project kickoff |
> | 1.1 | 2026-01-24 | Added Rule P-03 after production schema incident |
> | 1.2 | 2026-02-08 | Added Rule A-03 after deployment-path breakage |

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
<!--=============================================================-->

---

## Quick-Start Summary

*This section is reference material. It is not part of your Claude Project Brief. Do not copy it into your Brief.*

---

### Who this is for

This template is for people using Claude.ai chat projects to build things across multiple sessions. It is not for Claude Code users. It is not for API developers.

It is particularly suited to vibe coding. Vibe coding gets things built fast. The problem is that speed has a hidden cost. Decisions accumulate in chat threads. Rules get discovered and forgotten. Claude starts fresh every session while you carry all the context in your head. The Claude Project Brief is what stops that from becoming a problem.

If you are an experienced developer with engineering discipline already in place, this template still has value. But you will take less from it and need to adapt it more heavily to fit what you already do.

---

### Why bother

Many Claude projects suffer from the same structural gap: no formal opening and no formal close. Each thread starts from scratch, ends without ceremony, and decisions made inside it exist only in that thread.

**You stop repeating yourself.** Without a Brief, you re-explain your stack and constraints at the start of every session. With one, Claude already knows.

**You accumulate knowledge instead of losing it.** A rule discovered in session 4 is still enforced in session 40.

**Your sessions have a defined start and end.** Work is never left in an undocumented state.

**Mistakes stop recurring.** Once a rule is in the Brief, Claude does not repeat that mistake even in a session where you forgot to mention it.

**Context rot is caught early.** Research confirms that as threads grow longer, Claude's recall degrades. The self-refinement check in Session Open Discipline catches this before it causes damage.

**You can onboard anyone mid-project.** The Brief is a complete onboarding document for any new colleague or new Claude session joining the project.

**The discipline compounds.** The Brief gets more valuable the longer you maintain it.

---

### Common objections

**"I already have Git, Jira, and sprint planning. This feels like duplication."**

It is not duplication. It is a bridge. Claude's integrations with GitHub and Jira are session-triggered. You ask, Claude fetches. The Brief is different in kind. It is always loaded, active from the first word of every session without you doing anything. And the things it holds are not things you would ever put in a ticket: hard-won environmental constraints and failure patterns that live nowhere in your existing tooling.

**"I already use Claude Memory and Custom Instructions."**

They do a different job. Memory and Instructions tell Claude who you are, account-wide and general. The Brief tells Claude how this specific project works and what has gone wrong before. It is project-specific, versioned, and grows with the project. The three work well together. Memory and Instructions set the baseline. The Brief layers project-specific precision on top.

**"Is this just the Karpathy CLAUDE.md with a different name?"**

No, but they are related. The Karpathy file tells Claude how to think and code in general. The Brief tells Claude how this specific project works and what has already gone wrong. The Karpathy file itself says: "Merge with project-specific instructions as needed." That sentence is what this template is. A mature project benefits from having both.

| | Karpathy CLAUDE.md | Claude Project Brief |
|---|---|---|
| Scope | Universal, identical for every project | Project-specific, different content per project |
| Grows over time? | No, static | Yes, accumulates rules as failures occur |
| Session discipline | None | Core purpose |
| Target tool | Claude Code | Claude.ai chat projects |

---

### Opening prompt: auto-generating your Brief from existing project documents

If your Claude project already has documents in its knowledge area, paste this prompt to generate a draft Brief automatically:

*"I have uploaded a Claude Project Brief template to this project. Using that template as your guide, help me create a Claude Project Brief for [brief description of your project: what it does, what tech stack it uses, what environment it runs on]. Generate a part-filled version with the structure in place and placeholders where you need more information from me. Draw on any documents already in the project knowledge area, and on any project memory or custom instructions, to pre-populate as much as possible. Ask me questions as you go to fill in anything that cannot be inferred from existing context."*

---

*Claude-Project-Brief-Template-v1.8. Built from a real production project, validated across multiple independent projects. Freely adaptable for any project. British English throughout.*
