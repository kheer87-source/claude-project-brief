# Claude Project Brief: Universal Template

---

> **What is this file?**
> This is a template for creating a Claude Project Brief, a project rules document used inside a Claude AI project.
>
> **Two things to know before reading further.**
>
> **1. This template is specific to Claude.ai chat projects.** It works through the project knowledge area in Claude.ai. It is not designed for Claude Code, the Anthropic API, or third-party Claude integrations. If you are using Claude Code, look at the Karpathy CLAUDE.md convention instead. If you are using Claude.ai chat projects to build things across multiple sessions, this is for you.
>
> **2. This template is particularly suited to vibe coding.** Vibe coding is the pattern where someone builds real things with an AI assistant through natural conversation, iterating quickly without formal engineering discipline in place. It gets things built fast. The Claude Project Brief is what stops that speed from working against you as the project grows. It adds the session structure, failure memory, and context discipline that vibe coding is otherwise missing. If you are an experienced developer with established engineering practice already in place, this template still has value but you will need less of it.
>
> When you add a Claude Project Brief to your Claude project knowledge area, Claude reads it at the start of every session and applies its rules automatically. Think of it as a standing instruction manual that travels with every conversation in your project.
>
> This template was extracted from a real production project. The structure and session discipline patterns are the transferable insight. The content is yours to fill in.
>
> It was then tested against several other independent projects, each of which had been running with its own copy-and-paste notepad as a makeshift session memory. The template worked across all of them. Different projects, different tech stacks, same problem, same fix.
>
> **How to use this template:**
>
> **Starting a new project from scratch:**
> 1. Copy this file and name it `Claude Project Brief.md` or `[Your Project Name] Claude Project Brief.md` if you want to prefix it with your project name
> 2. Work through each section. The hints (shown in blockquotes like this one) explain what to write
> 3. Delete the hints and the worked example once your version is complete
> 4. Upload the finished file to your Claude project knowledge area
> 5. From that point on, Claude will apply your rules automatically in every session
>
> **Using this template on an existing project:**
> If your Claude project already has documents in its knowledge area (a technical architecture, business requirements document, product blueprint, data dictionary, or build guides) you do not need to fill this template in manually. Claude can read those documents and generate a part-filled Claude Project Brief for you automatically. Paste the opening prompt from the Quick-Start Summary at the end of this file to begin that process.
>
> Claude will also draw on your project's memory and any custom instructions you have set. These contain background context, preferences, and technical detail that Claude uses to pre-populate sections such as the authority hierarchy, stack-specific rules, and session discipline steps. This significantly reduces the amount you need to type.
>
> In both cases, the output is a draft. Review it, correct anything that does not match reality, and add the rules that only you know from lived experience on the project.
>
> **A worked example is included throughout.** It uses a fictitious project called *Birchwood Booking*, a simple web-based room booking system. The example appears in grey blockquotes labelled **EXAMPLE** alongside each section. It shows you what a populated version looks like. Remove it from your own file.

---

## Section 1: Document Header Block

> **What goes here:** The frontmatter block at the very top of the file. Claude uses the `description` field to decide when to load this document. Write it to trigger on any mention of your project name, technology stack components, or key feature terms. Be generous. It is better to trigger too often than to miss a session where the rules were needed.
>
> **Format:** Replace everything below with your own project details.

```
---
name: [your-project-slug]
description: Non-negotiable engineering rules, session discipline, and conventions for [Your Project Name]. ALWAYS retrieve this skill at the start of any session involving [Your Project Name]: writing code, running SQL, editing configuration, deploying, or answering architecture questions. Retrieve this skill before any other tool or search. If the user mentions any of the following, this skill is mandatory: [list your key tech terms, feature names, server names, file names].
---
```

> **EXAMPLE →**
> ```
> ---
> name: birchwood-booking
> description: Non-negotiable engineering rules, session discipline, and conventions for the Birchwood Booking web application. ALWAYS retrieve this skill at the start of any session: writing code, running migrations, editing config, or answering architecture questions. If the user mentions any of the following, this skill is mandatory: Birchwood, booking, Laravel, MySQL, Nginx, Blade, Tailwind, server, migration, seed, deploy.
> ---
> ```

---

## Section 2: Opening Statement

> **What goes here:** Two or three sentences at the top of the document body that establish what this file is and why it exists. The key phrase to include: *"every rule here exists because its violation caused a real failure."* This tells Claude (and future colleagues) that these rules are not preferences. They are lessons learned from real mistakes.

```markdown
# [Your Project Name]: Claude Project Brief

This document is the authoritative source of non-negotiable rules for all [Your Project Name] development work. It is not a reference document. It is a project rules document. Every rule here exists because its violation caused a real failure in a real session.
```

> **EXAMPLE →**
> ```markdown
> # Birchwood Booking: Claude Project Brief
>
> This document is the authoritative source of non-negotiable rules for all Birchwood Booking development work. It is not a reference document. It is a project rules document. Every rule here exists because its violation caused a real failure in a real session.
> ```

---

## Section 3: Authority Hierarchy

> **What goes here:** A three-layer hierarchy that tells Claude how to resolve conflicts between what it sees in the live session, what this file says, and any background memories it holds. This section prevents Claude from overriding hard-won rules because something "appeared to work differently today."
>
> The three layers are always the same in structure. Only the layer names differ slightly per project. Customise the Layer 2 description to reflect your own distinction between permanent environment rules and current state rules.

```markdown
**Authority hierarchy: three layers**

**Layer 1: Live conversation context.** Whatever is discovered, fixed, or decided within the current session thread is the ground truth for that session. No document overrides direct evidence from the running system.

**Layer 2: This Claude Project Brief.** Two types of rules live here:
- *Structural rules*: environment constraints that never change regardless of session outcomes ([give examples: server access method, file transfer method, approved terminal commands]). These cannot be overridden by Layer 1 even if something appears to work without following them. The failure mode is probabilistic, not guaranteed every time.
- *Architectural state rules*: current state of the codebase ([give examples: column names, file paths, service names, approved vocabulary]). A deliberate architectural change in a live session supersedes these. That is also the moment the Claude Project Brief must be updated at session close.

**Layer 3: Background context and project memory.** Useful supporting context: background, preferences, session patterns. Where it conflicts with this Claude Project Brief, treat it as a signal that the Claude Project Brief may need updating rather than that the background context is authoritative.
```

> **EXAMPLE →**
>
> **Layer 1: Live conversation context.** Whatever is discovered, fixed, or decided within the current session thread is the ground truth for that session.
>
> **Layer 2: This Claude Project Brief.** Two types of rules live here:
> - *Structural rules*: how to connect to the server, which branch to work on, how to run migrations. These cannot be overridden.
> - *Architectural state rules*: current table names, column names, route prefixes, approved CSS class conventions. A deliberate change in a live session supersedes these. That is also the moment the Claude Project Brief must be updated.
>
> **Layer 3: Background context.** Useful context about preferences and patterns. Where it conflicts with this Claude Project Brief, treat it as a prompt to update the Claude Project Brief rather than override it.

---

## Section 4: How to Find Authoritative Documents

> **What goes here:** A short navigation guide telling Claude where to find the definitive version of key project documents (build guides, architecture diagrams, migration files, etc.). The key principle: always use the highest version number; never hardcode a version in memory.
>
> Adapt the examples to match whatever you call your own documents.

```markdown
## How to Find Authoritative Documents

To find the current authoritative document for any area, search project knowledge for `[DocumentNamePattern]` and use the result with the highest version number. Never hardcode a version. Never assume a version from memory.

Examples:
- [Area 1] guide → search `[Pattern]`, use highest version
- [Area 2] guide → search `[Pattern]`, use highest version
```

> **EXAMPLE →**
>
> ## How to Find Authoritative Documents
>
> Search project knowledge for the document name and use the result with the highest version number. Never assume a version from memory.
>
> - Database migration guide → search `Birchwood-Migration-Guide`, use highest version
> - Deployment guide → search `Birchwood-Deploy-Guide`, use highest version
> - UI component library → search `Birchwood-UI-Spec`, use highest version

---

## Section 5: Session Open Discipline

> **What goes here:** The mandatory steps Claude must complete at the start of every session, before any code or commands are produced. At minimum this should cover: confirming session continuity, confirming documents are uploaded, taking any safety snapshots or backups appropriate to your environment, and, critically, a self-refinement check.
>
> **Why the self-refinement check matters: context rot.**
> Research has confirmed what many Claude users discover through experience: as a chat thread grows longer, Claude's recall of earlier instructions degrades. This is known as "context rot." Claude's context window processes everything in one shared buffer. Your messages, Claude's replies, uploaded files, and the Project Brief all compete for the same space. Performance follows a U-shaped curve, with best recall at the very beginning and end of the context window, and worst recall in the middle. As a thread grows, your Project Brief drifts toward that dead zone.
>
> The fix is simple and takes seconds: at the start of every session, instruct Claude to confirm it has read and is actively applying the Claude Project Brief. If a thread has grown long, instruct Claude to re-read the Brief before continuing. This self-refinement check catches context fade before it causes a mistake rather than after.
>
> If you use version control (Git), a snapshot step might be replaced by "confirm the working branch and that it has no uncommitted changes." If you use database backups, name the backup command here.

```markdown
## Session Open Discipline: Mandatory Before Any Work

1. Confirm you have read and are actively applying the Claude Project Brief for this project.
   If this thread is long or context feels thin, re-read the Brief now and confirm which
   version you are working from before proceeding.
2. Confirm the session number or reference. Ask if not clear.
3. Confirm all documents from the previous session have been uploaded or committed.
   Do not proceed until confirmed.
4. [Take a snapshot / create a backup / confirm Git branch state]:
   [Insert your specific commands or steps here]
5. If any design questions are unresolved, resolve them fully before writing any code.
```

> **EXAMPLE →**
>
> ## Session Open Discipline: Mandatory Before Any Work
>
> 1. Confirm you have read and are actively applying the Birchwood Booking Claude Project Brief.
>    If this thread is long, re-read the Brief now and confirm the version before proceeding.
> 2. Confirm the session reference. Ask if not clear.
> 3. Confirm the previous session's migration files and notes have been committed to the `dev` branch.
> 4. Create a database backup before any schema changes:
>    ```
>    On the server console:
>    mysqldump -u root -p birchwood_db > /var/backups/birchwood_pre_session.sql
>    ```
> 5. Confirm the working branch is `dev`, not `main`. Never work directly on `main`.
> 6. If any design questions are unresolved, resolve them before writing any code.

---

## Section 6: Session Close Gate

> **What goes here:** A sequential checklist that must be completed before declaring a session closed. This is the most important section. It is what prevents knowledge from living only in a chat thread and disappearing. Work through every step in order.
>
> The standard steps are: snapshots/backups, updated guides, handover note, backlog/ticket update, Claude Project Brief update if needed, thread sweep, then upload/commit. Adapt the names and tools to your project.

```markdown
## Session Close Gate: Complete in Order Before Closing

**Step 1: Snapshot, Backup, or Commit**
[Describe the save-state action appropriate to your environment.]

**Step 2: Updated documentation**
Updated guide produced for every area touched this session. Version number incremented.

**Step 3: Handover note produced, covering:**
- Summary of what was done
- Current state of every in-progress item
- Lessons learnt, including any new rules discovered this session
- Next session priority list
- Footer: "Upload / commit before opening next session"

**Step 4: Backlog or ticket tracker updated**
New items added. Status changes recorded. Decisions logged.

**Step 5: Claude Project Brief updated if required**
If any new non-negotiable rule was discovered this session, add it here before closing. One rule, one entry.

**Step 6: Thread sweep**
Read back through the session. Ask: is there any decision, discovery, or constraint that exists only in this conversation and has not been captured in a document? If yes, capture it before closing.

**Step 7: Upload or commit**
All produced documents uploaded or committed. Confirm before closing.
```

> **EXAMPLE →**
>
> ## Session Close Gate
>
> **Step 1: Commit**
> Commit all changed files to `dev` branch with a descriptive message. Never leave uncommitted work at session end.
>
> **Step 2: Updated guides**
> Update the migration guide and deploy guide if any schema or deployment steps changed this session.
>
> **Step 3: Handover note** covering: what was built, current state, lessons learnt, next priority list.
>
> **Step 4: GitHub Issues or project board** updated with any new or resolved items.
>
> **Step 5: Claude Project Brief updated** if any new rule was discovered.
>
> **Step 6: Thread sweep.** Anything discovered only in chat that hasn't been committed?
>
> **Step 7: Push** the `dev` branch and confirm the push was accepted.

---

## Section 7: Non-Negotiable Rules

> **What goes here:** The core of the document. Each rule is a specific, testable constraint. Rules are grouped by category (terminal/server, database, file transfer, framework-specific, etc.). Each rule has:
> - A unique code (e.g. `T-01`, `P-01`, `F-01`) so it can be referenced unambiguously
> - A short bold title
> - One or two sentences of explanation
> - Optionally: the exact command to use, or the exact wrong command to never use
>
> **How to discover your own rules:** Look at your past mistakes. Every time something broke because you did it the wrong way, that's a rule. Common categories are shown below. Add or remove categories to match your stack.
>
> Start with a small number of real rules. Do not invent rules speculatively. Rules are added when violations cause real failures, not in advance.

---

### Category T: Terminal and Server Access Rules

> **What goes here:** Rules about how to connect to and operate on your server(s). Common rules in this category cover: which user to run commands as, which shell to avoid, how not to write files to the server, approved connection methods.

```markdown
## Non-Negotiable Terminal and Server Rules

**Rule T-01: [Title]**
[One or two sentences. State the rule positively and negatively. "Always do X. Never do Y."]

**Rule T-02: [Title]**
[etc.]
```

> **EXAMPLE →**
>
> **Rule T-01: Always connect via SSH as the `deploy` user, never as `root`**
> The `root` account on the Birchwood server is locked for interactive sessions. Always `ssh deploy@birchwood.example.com`. If a command needs elevated privileges, use `sudo`.
>
> **Rule T-02: Never write files using `echo` one line at a time**
> Multi-line files written with repeated `echo >>` produce inconsistent line endings. Always use `nano`, transfer via SCP/SFTP, or use a heredoc only when the file contains no special characters.

---

### Category P: Database Rules

> **What goes here:** Rules for your database engine. Cover: which user to connect as, which database name to use for which environment, how to safely run schema changes, how to handle enum-style columns, sequence/auto-increment behaviour.

```markdown
## Non-Negotiable Database Rules

**Rule P-01: [Title]**
[Rule text.]

**Rule P-02: [Title]**
[etc.]
```

> **EXAMPLE →**
>
> **Rule P-01: Always connect as `birchwood_app`, never as `root`, for application queries**
> The `root` MySQL user has global privileges. Application queries always use `mysql -u birchwood_app -p birchwood_db`. The `root` user is only used for `mysqldump` backups and schema privilege grants.
>
> **Rule P-02: Always `DESCRIBE tablename` before writing any query**
> Never assume column names from memory. Run `DESCRIBE tablename;` before writing any INSERT, UPDATE, or SELECT. One `DESCRIBE` check before writing saves a failed query.
>
> **Rule P-03: Run migrations on `dev` database and verify before running on `production` database**
> Never run an untested migration on the production database. Test on `birchwood_dev`, confirm the result, then run on `birchwood_db`.

---

### Category F: File Transfer Rules

> **What goes here:** Rules for how files move between your local machine and the server (or between environments). Cover: which method is approved, which file types must use which method, what to verify after transfer.

```markdown
## Non-Negotiable File Transfer Rules

**Rule F-01: [Title]**
[Rule text.]
```

> **EXAMPLE →**
>
> **Rule F-01: Transfer all PHP, JS, and CSS files via SCP or SFTP only**
> Never paste file content directly into a terminal session. Even short files lose indentation and special characters when pasted. Use `scp localfile.php deploy@birchwood.example.com:/var/www/birchwood/`.
>
> **Rule F-02: After any file transfer, verify with `md5sum` on both sides**
> Confirm the transferred file is byte-identical to the source before restarting any service.

---

### Category A: Application and Framework Rules

> **What goes here:** Rules specific to the framework or runtime your application uses. Examples: route ordering, caching behaviour, build commands, environment variable management, third-party library quirks discovered in practice.

```markdown
## Non-Negotiable Application and Framework Rules

**Rule A-01: [Title]**
[Rule text.]
```

> **EXAMPLE →**
>
> **Rule A-01: Always run `php artisan config:clear` after any `.env` change**
> Laravel caches the config. A changed `.env` value is not picked up until the cache is cleared. Always run `php artisan config:clear && php artisan cache:clear` on the server after editing `.env`.
>
> **Rule A-02: Never run `php artisan migrate` on the production server without a backup**
> Always run Step 1 of the Session Open Discipline (the `mysqldump` backup) before any `migrate` on production. The backup must complete before the migration begins.
>
> **Rule A-03: Named routes must be used in all Blade templates. Never hardcode URLs.**
> `href="{{ route('bookings.index') }}"` is correct. `href="/bookings"` is wrong. Hardcoded URLs break when the application is served from a subdirectory.

---

### Category D: Diagnostic Rules

> **What goes here:** Rules for how to investigate problems. The most important rule in this category is always: diagnose completely before producing any fix. Cover: where logs are, how to read them, how to avoid treating symptoms rather than causes.

```markdown
## Non-Negotiable Diagnostic Rules

**Rule D-01: Diagnose completely before producing any fix**
[Expand on this for your environment.]
```

> **EXAMPLE →**
>
> **Rule D-01: Diagnose completely before producing any fix**
> Never make one-fix-at-a-time passes without root cause analysis first. Read the Laravel log (`storage/logs/laravel.log`), identify the exact error and line, confirm the cause from evidence, then write the fix.
>
> **Rule D-02: Check the Nginx error log before assuming the application is at fault**
> A 502 Bad Gateway is Nginx failing to reach PHP-FPM, not an application error. Always check `/var/log/nginx/error.log` first.

---

### Category G: Governance Rules

> **What goes here:** Rules about how decisions are made and recorded, particularly decisions that are hard to reverse. Cover: who must be consulted before certain changes, how decisions are recorded, what changes require explicit approval, how documentation is versioned.

```markdown
## Non-Negotiable Governance Rules

**Rule G-01: Code must only ADD features without explicit approval to remove**
[Expand on your team's approval process.]

**Rule G-02: Default output format is [Markdown / Word / etc.]**
[State your team's standard.]
```

> **EXAMPLE →**
>
> **Rule G-01: No feature may be removed without a recorded team decision**
> All feature removals require a note in the project log with the date, reason, and who approved. Code that is removed must be referenced in a git commit message explaining why.
>
> **Rule G-02: Default output format is Markdown `.md`**
> All session notes, guides, and handover documents are produced in Markdown unless explicitly requested otherwise.
>
> **Rule G-03: Any change to the database schema requires a migration file. Never use a manual `ALTER TABLE`.**
> Direct schema changes on the server are not tracked, cannot be replicated to other environments, and cannot be rolled back. All schema changes go through `php artisan make:migration`.

---

## Section 8: Self-Validation Checklist

> **What goes here:** A table of checks that Claude runs through internally before producing any output. The discipline: Claude must not produce any code, SQL, or terminal commands until all applicable checks pass. Populate this table with the checks most relevant to your project's failure modes.
>
> The checks should map directly to your rules above. If Rule P-02 says "always `DESCRIBE tablename` first", then the checklist should have a row: "4 | `DESCRIBE tablename` run before any SQL written? | Any SQL".

```markdown
## Self-Validation Checklist

Before producing any output (code, SQL, terminal commands, or file content) run through this checklist internally. Do not skip steps.

| # | Check | Applies when |
|---|---|---|
| 1 | Session reference confirmed and previous documents uploaded/committed? | Session open |
| 2 | Safety snapshot, backup, or branch check completed? | Session open |
| 3 | Authoritative document for relevant area retrieved (highest version)? | Any work involving a documented area |
| 4 | `DESCRIBE tablename` or equivalent schema check run before any SQL? | Any SQL |
| 5 | File transfer method confirmed as appropriate for file type? | Any file transfer |
| 6 | [Framework-specific check, e.g. config cache cleared?] | [Relevant trigger] |
| 7 | Design questions fully resolved before first line of code? | Any build session |
| 8 | Labels and names describe only what is implemented, not what is intended? | Any UI or documentation |
| [Add rows for every significant rule in your project] | | |
```

> **EXAMPLE →**
>
> | # | Check | Applies when |
> |---|---|---|
> | 1 | Session reference confirmed and previous work committed? | Session open |
> | 2 | `mysqldump` backup completed? | Before any migration |
> | 3 | Working branch confirmed as `dev`, not `main`? | Session open |
> | 4 | `DESCRIBE tablename` run before any query? | Any SQL |
> | 5 | File transferred via SCP/SFTP, not pasted into terminal? | Any file transfer |
> | 6 | `php artisan config:clear` run after any `.env` change? | Any environment config change |
> | 7 | Migration tested on `birchwood_dev` before production? | Any migration |
> | 8 | Named routes used, no hardcoded URLs in Blade templates? | Any frontend template |
> | 9 | Nginx and Laravel logs read before assuming application fault? | Any 5xx error |
> | 10 | Design questions fully resolved before first line of code? | Any build session |

---

## Section 9: Version History

> **What goes here:** A simple table tracking changes to this Claude Project Brief itself. Every time a new rule is added (because a violation caused a real failure), log it here with the date and a brief description of what was added. This gives future colleagues context for why each rule exists.

```markdown
## Version History

| Version | Date | Change |
|---|---|---|
| 1.0 | [YYYY-MM-DD] | Initial: rules established at project start |
| 1.1 | [YYYY-MM-DD] | Added [Rule X] after [brief description of what went wrong] |
```

> **EXAMPLE →**
>
> | Version | Date | Change |
> |---|---|---|
> | 1.0 | 2026-01-10 | Initial: rules established at project kickoff |
> | 1.1 | 2026-01-24 | Added Rule P-03 after production schema incident |
> | 1.2 | 2026-02-08 | Added Rule A-03 after deployment-path breakage |

---

## Section 10: Footer

> **What goes here:** A brief footer that states this document's authority and maintenance instructions. Keep it short.

```markdown
---

*This document is the authoritative constraint register for [Your Project Name].*
*Authority hierarchy: live session context, then this Claude Project Brief (structural rules), then background context.*
*When a new non-negotiable rule is discovered, add it here before the session closes. One rule, one entry.*
*British English throughout.* [Or: American English / your team's standard]
```

---

## Quick-Start Summary for New Users

> This section is for colleagues picking up this template for the first time. It can be kept in your finished Claude Project Brief or removed once the team is familiar with the format.

---

### Why bother with a Claude Project Brief?

**Before anything else: who this is for.**

This template is for people using Claude.ai chat projects to build things across multiple sessions. It is not for Claude Code users. It is not for API developers. It is specifically for the Claude.ai project environment where your knowledge area, memory, and chat threads are your working infrastructure.

It is particularly suited to vibe coding. Vibe coding gets things built fast. You describe what you want, Claude builds it, you iterate, the project grows. The problem is that speed has a hidden cost. Decisions accumulate in chat threads. Rules get discovered and forgotten. Claude starts fresh every session while you carry all the context in your head. The Claude Project Brief is what stops that from becoming a problem. It adds the structure, discipline, and failure memory that vibe coding is otherwise missing.

If you are an experienced developer with engineering discipline already in place, this template still has value. But you will take less from it and need to adapt it more heavily to fit what you already do.

Many development projects using Claude work well session by session. They suffer, however, from the same structural gap: **no formal opening, and no formal close.** Each chat thread starts from scratch, ends without ceremony, and the decisions made inside it exist only in that thread. The next session, Claude has no memory of what was agreed, what failed, or what the rules were.

A Claude Project Brief addresses this directly. Here is what changes when you use one:

**You stop repeating yourself.** Without a Claude Project Brief, you re-explain your stack, your constraints, and your preferences at the start of every session. With one, Claude already knows. It reads the file before you type a word.

**You accumulate knowledge instead of losing it.** Every session adds to the constraint register. A rule discovered in session 4 is still enforced in session 40. Without this file, that rule lives in your memory alone.

**Your sessions have a defined start and end.** The Session Open Discipline means every session begins with safety checks. The Session Close Gate means every session ends with documentation, not just a closed browser tab. Work is never left in an undocumented state.

**Mistakes stop recurring.** Rules exist because violations caused real failures. Once a rule is in the Claude Project Brief, Claude will not repeat that mistake, even in a session where you forgot to mention it.

**Context rot is caught before it causes damage.** Research has confirmed that as chat threads grow longer, Claude's recall of earlier instructions degrades. This pattern is known as context rot. Performance follows a U-shaped curve, worst in the middle of a long thread. The self-refinement check built into the Session Open Discipline catches this early. If context is thin, Claude re-reads the Brief before proceeding. The fix is a single instruction and takes seconds.

**You can bring in a colleague or a new Claude session mid-project.** The Claude Project Brief is a complete onboarding document for anyone joining the project, whether human or a new AI session. It tells them the environment, the constraints, the current state, and the history of decisions. No catch-up conversation needed.

**The discipline compounds.** Projects without formal session structure tend to accumulate technical debt and undocumented decisions. Projects with this structure accumulate the opposite: a growing, reliable constraint register that makes each session faster and safer than the last.

---

### Addressing common objections

**"I already have proper development discipline: tickets, Git, code review, sprint planning. This feels like duplication."**

It is not duplication. It is a bridge, and the distinction matters.

Claude does have integrations with GitHub, Jira, Google Drive, and other tools. When those integrations are active, Claude can query a ticket or read a commit when you ask it to. But those integrations are *session-triggered*. Claude fetches what you explicitly request in a given conversation. They are not a persistent, always-loaded context. The Claude Project Brief is different in kind. It is read automatically at the start of every session, before you type a word, and its rules are active throughout without you having to invoke them.

More importantly, the things your Claude Project Brief holds are not things you would ever put in a Jira ticket or a commit message. "The `users` table column was renamed three months ago. The old name still appears in legacy documentation and causes silent query failures." "This deployment script breaks if run as root. We discovered this after two failed releases." These are hard-won environmental constraints and failure patterns. They live nowhere in your existing tooling because no existing tool was designed to hold them.

Think of it this way: your PM discipline governs what your team does. Your Git history records what changed. Your Claude Project Brief governs what Claude does on your behalf, informed by everything your team has learned. The three operate in different lanes. A strong team with strong discipline gets the most value from a Claude Project Brief. The rules are already clear and just need to be written down once in a place Claude can read.

---

**"I already use Claude Memory and Custom Instructions. This looks like duplication of that."**

Claude Memory and Custom Instructions are genuinely useful. They do, however, operate at the wrong level of granularity for project-specific constraint management. Understanding the distinction matters:

*Claude Memory* captures things about you as a person and user: your preferences, your background, your working style. It is account-wide and general. It tells Claude who you are. It does not tell Claude how a specific system is built, what has broken before in a specific codebase, or what the non-negotiable rules are for a specific database schema.

*Custom Instructions* set broad behavioural defaults: tone, format, approach. Again, account-wide and general. They are not versioned, not project-specific, and not able to carry the kind of precise technical constraint that a Claude Project Brief holds.

*A Claude Project Brief* is project-specific, versioned, and grows with the project. It holds things that Memory and Instructions cannot: "the `users` table column was renamed three months ago and the old name still appears in legacy documentation causing silent query failures"; "never run the deployment script as root on this server because it breaks in a way that is not obvious from the error message"; "authentication middleware must be registered before route handlers in this framework or requests bypass it silently."

Memory and Instructions give Claude general context about you. The Claude Project Brief gives Claude specific, hard-won, project-level constraints that took real failures to discover. The three work well together. Memory and Instructions set the baseline. The Claude Project Brief layers the project-specific precision on top.

If you are already using Memory and Instructions effectively, adding a Claude Project Brief is a natural next step, not a replacement. You will find that the Claude Project Brief captures the things you keep having to re-explain in individual sessions because they are too specific for Memory and too detailed for Instructions.

---

**"This looks similar to the Karpathy CLAUDE.md guidelines. Is this just the same thing with a different name?"**

This is the sharpest challenge, so it deserves a precise answer rather than a diplomatic one.

The Karpathy CLAUDE.md (github.com/multica-ai/andrej-karpathy-skills) is a 65-line file that encodes four universal AI coding behaviour principles: think before coding, simplicity first, surgical changes, goal-driven execution. It has 165,000 GitHub stars and is one of the fastest-growing repositories in GitHub's history. It is excellent and you should use it.

Here is what it is not. It is not project-specific, it does not grow, it has no session discipline, and it has no memory of what has gone wrong before. The file itself says: *"Merge with project-specific instructions as needed."* That sentence is what this template is.

The precise comparison:

| | Karpathy CLAUDE.md | This Claude Project Brief Template |
|---|---|---|
| Scope | Universal, identical for every project | Project-specific, different content per project |
| Content | General AI behaviour principles | Project constraints, environment rules, failure history |
| Grows over time? | No, static | Yes, accumulates rules as failures occur |
| Session discipline | None | Core purpose |
| Failure memory | None | Central purpose |
| Target tool | Claude Code (terminal) | Claude.ai chat projects |

If your Claude Project Brief contains a section that duplicates Karpathy's four principles verbatim, simplify. Those principles are already covered if you have the Karpathy guidelines loaded. Your Claude Project Brief should focus on what Karpathy cannot cover: your specific environment, your specific failure history, your session open and close discipline.

The honest summary: Karpathy tells Claude how to think and code in general. Your Claude Project Brief tells Claude how *this* system works and what has broken before. A mature project benefits from having both. The Karpathy guidelines serve as the universal baseline. The Claude Project Brief sits as the project-specific layer on top. They are complementary, not competing.

---

1. **This file travels with your project.** Upload it to your Claude project knowledge area. Claude reads it automatically at the start of every session.

2. **Rules are discovered, not invented.** Start with a small set of real rules, things that actually went wrong. Add rules only when violations cause real failures. Your first version may have 10 rules. That is correct. A mature project may accumulate 50 or more over many sessions.

3. **The session open and close gates are the most important sections.** The number one cause of lost work in AI-assisted development is knowledge that lives only in a chat thread. The close gate forces that knowledge into documents before the thread ends.

4. **Rule codes matter.** Using `Rule P-03` instead of "the migration rule" gives you a way to refer to a specific rule without ambiguity. Claude will also reference them in its explanations, making it easy to trace why it is doing something.

5. **Update this file at session close.** If you discover a new non-negotiable rule in a session, add it before closing. The Claude Project Brief is only as useful as its most recent update.

---

### Opening prompt: generating a part-filled Claude Project Brief from your existing project

If your Claude project already has documents in its knowledge area, or has project memory and custom instructions set, paste this prompt to generate a draft Claude Project Brief automatically:

> *"I have uploaded a Claude Project Brief template to this project. Using that template as your guide, help me create a Claude Project Brief for [brief description of your project: what it does, what tech stack it uses, what environment it runs on]. Generate a part-filled version with the structure in place and placeholders where you need more information from me. Draw on any documents already in the project knowledge area, and on any project memory or custom instructions, to pre-populate as much as possible. Ask me questions as you go to fill in anything that cannot be inferred from existing context."*

Claude will read the template, cross-reference your existing project documents and memory, populate what it can, mark the gaps clearly, and ask targeted questions to fill them. One or two rounds of back-and-forth will produce a working v1.0 ready to upload as your active project skill.

---

*Claude-Project-Brief-Template-v1.7. Built from a real production project, validated across multiple independent projects. Freely adaptable for any project. British English throughout.*
