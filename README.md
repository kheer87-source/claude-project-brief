# Claude Project Brief

A template for adding session discipline, failure memory, and project-specific rules to your Claude.ai projects.

---

## The problem it solves

I was building a commercial IoT (Internet of Things) monitoring platform on Claude.ai. Dozens of sessions, hundreds of decisions. Rules figured out the hard way. Architectural calls that took multiple sessions to reach.

And they kept disappearing.

Not the code. The context. Every time I opened a new chat thread, Claude started fresh. I didn't. My first fix was embarrassingly simple: a plain text notepad. I kept rough session notes and copy-pasted the bits Claude needed into the next thread. It worked. It was also a chore and I knew it wouldn't scale.

So I built something better. I then tested it across numerous other solutions I had developed. It worked across every one. Different projects, different tech stacks, same problem, same fix.

---

## Who this is for

People using Claude.ai chat projects to build things across multiple sessions.

It is not for Claude Code. It is not for the Anthropic API. It is specifically for the Claude.ai project environment.

It is particularly suited to vibe coding: building real things through natural conversation with Claude, iterating fast, without formal engineering process in place. Vibe coding gets things built fast. The Claude Project Brief is what stops that speed from working against you as the project grows.

If you are an experienced developer with established engineering discipline already in place, this template still has value. But you will take less from it and need to adapt it more to fit what you already do.

---

## What it adds

**Session discipline.** Every session opens with a defined checklist and closes with a structured handover. Decisions do not live in chat threads. They get captured before the thread closes.

**Failure memory.** Every rule in the Brief exists because breaking it caused a real failure. Claude reads it at the start of every session. It does not repeat the same mistake in session 40 that it made in session 4.

**Versioning.** The Brief grows with the project. The longer you use it, the more valuable it gets. It is not a static config file. It is a living constraint register. Every time a session uncovers a new rule, you add it before closing. That is what keeps it useful.

**Auto-generation.** If your Claude project already has documents in the knowledge area, architecture docs, business requirements, a product blueprint, Claude can read them and generate a populated Brief automatically. You do not start from a blank page.

---

## Context rot and the self-refinement check

If a chat thread runs very long, Claude's recall of the Brief can fade. Research calls this context rot. As a thread grows, earlier instructions drift toward the middle of the context window, which is exactly where recall is weakest. It is not a flaw unique to Claude. It is how large language models work.

The fix is simple. Keep threads focused. Open each new one with a one-line instruction telling Claude to re-read the Brief. The template builds this check into the session open discipline as a mandatory first step.

---

## What it is not

It does not replace Claude Memory or Custom Instructions. Those tell Claude who you are, account-wide and general. The Claude Project Brief tells Claude how this specific project works and what has gone wrong before. They do different jobs and work well together.

It is not a competitor to the Karpathy CLAUDE.md convention. That file tells Claude how to think and code in general. The Brief tells Claude how your specific project works. A mature project benefits from having both.

---

## How to use it

**Option 1: New project, starting from scratch**

1. Download [`Claude-Project-Brief-Template-with-examples.md`](https://github.com/kheer87-source/claude-project-brief/blob/main/Claude-Project-Brief-Template-with-examples.md)
2. Work through each section. The hints explain what to write. The EXAMPLE blocks show a populated version using a fictitious project.
3. Delete the hints and examples when your version is complete.
4. Upload the finished Brief to your Claude project knowledge area.
5. Keep it updated. Every time a session uncovers a new rule, add it before closing the session. A Brief that stops being updated stops being useful.

**Option 2: Existing project with documents already in Claude**

1. Download [`Claude-Project-Brief-Template-blank.md`](https://github.com/kheer87-source/claude-project-brief/blob/main/Claude-Project-Brief-Template-blank.md) and upload it to your Claude project knowledge area alongside your existing documents.
2. Paste this prompt into a new chat:

*"I have uploaded a Claude Project Brief template to this project. Using that template as your guide, help me create a Claude Project Brief for [brief description of your project: what it does, what tech stack it uses, what environment it runs on]. Generate a part-filled version with the structure in place and placeholders where you need more information from me. Draw on any documents already in the project knowledge area, and on any project memory or custom instructions, to pre-populate as much as possible. Ask me questions as you go to fill in anything that cannot be inferred from existing context."*

3. Review the output. Correct anything that does not match reality. Add the rules only you know from lived experience.
4. Upload the finished Brief and keep it updated as the project develops.

---

## Repository contents

| File | Description |
|---|---|
| [`Claude-Project-Brief-Template-with-examples.md`](https://github.com/kheer87-source/claude-project-brief/blob/main/Claude-Project-Brief-Template-with-examples.md) | Full template with worked examples and guidance hints. Start here if you are new to this template. |
| [`Claude-Project-Brief-Template-blank.md`](https://github.com/kheer87-source/claude-project-brief/blob/main/Claude-Project-Brief-Template-blank.md) | Sections 1-10 only, hints but no examples. Use this once you understand the structure. |
| `README.md` | This file |

---

## Feedback

I have not found anything in the Claude community covering what the Brief does specifically: session discipline, failure memory, versioning, and auto-generation from existing project documents. If something exists and I have missed it, I would genuinely like to know. If it does not, this might be useful to someone.

---

*Tested on Claude.ai across multiple independent projects. Built from a real production project developed across 70+ sessions.*
