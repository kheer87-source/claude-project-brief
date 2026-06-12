Claude Project Brief

A template for adding session discipline, failure memory, and project-specific rules to your Claude.ai projects.

Who this is for

People using Claude.ai chat projects to build things across multiple sessions. Particularly relevant if you are vibe coding: building real things through natural conversation with Claude, iterating fast, without formal engineering process in place.

It is not for Claude Code. It is not for the Anthropic API. It is specifically for the Claude.ai project environment.

The problem it solves

When you use Claude across multiple sessions, context disappears. The rules figured out the hard way. The architectural decisions that took three sessions to reach. Claude starts fresh every time. You do not.

The longer a chat thread runs, the worse this gets. Research calls it context rot. Earlier instructions drift toward the middle of the context window, which is exactly where recall is weakest.

A Claude Project Brief fixes this. It lives in your Claude project knowledge area. Claude reads it at the start of every session before you type a word.

What it adds

Session discipline. Every session opens with a defined checklist and closes with a structured handover. Decisions do not live in chat threads.

Failure memory. Every rule in the Brief exists because breaking it caused a real failure. Claude does not repeat the same mistake in session 40 that it made in session 4.

Versioning. The Brief grows with the project. The longer you use it, the more valuable it gets.

Auto-generation. If your Claude project already has documents in the knowledge area, architecture docs, business requirements, a product blueprint, Claude can read them and generate a populated Brief automatically. You do not start from a blank page.

What it is not

It does not replace Claude Memory or Custom Instructions. Those tell Claude who you are. The Claude Project Brief tells Claude how this specific project works and what has gone wrong before. They do different jobs and work well together.

It is not a competitor to the Karpathy CLAUDE.md convention. That file tells Claude how to think and code in general. This tells Claude how your specific project works. A mature project benefits from having both.

How to use it

Download Claude Project Brief Template.md
Open a Claude.ai project
Paste this prompt into a new chat:

"I have uploaded a Claude Project Brief template to this project. Using that template as your guide, help me create a Claude Project Brief for [brief description of your project: what it does, what tech stack it uses, what environment it runs on]. Generate a part-filled version with the structure in place and placeholders where you need more information from me. Draw on any documents already in the project knowledge area, and on any project memory or custom instructions, to pre-populate as much as possible. Ask me questions as you go to fill in anything that cannot be inferred from existing context."

Review the output, add the rules only you know from experience, and upload the finished Brief to your project knowledge area
From that point on, Claude applies your rules automatically at the start of every session
Keep it updated. Every time a session uncovers a new rule, a broken assumption, or a hard-won constraint, add it to the Brief before closing the session. A Brief that stops being updated stops being useful. The value compounds the longer you maintain it. This is not a one-time setup. It is a living document.

Contents

FileDescriptionClaude Project Brief Template.mdThe full template with worked example and guidanceREADME.mdThis file

Context rot and the self-refinement check

If a chat thread runs very long, Claude's recall of the Brief can fade. The fix is simple. Keep threads focused. Open each new thread with a one-line instruction telling Claude to re-read the Brief. The template builds this check into the session open discipline as a mandatory first step.

Origin

Built from a real production project developed across 70+ sessions on Claude.ai. The copy-and-paste notepad that preceded it was not unique to that project. Several other independent projects were running the same workaround in parallel. The template was tested against all of them. It worked across every one. Different projects, different tech stacks, same problem, same fix.


Feedback

If you find this useful, have improved it, or have found something similar that already exists and I missed, I would genuinely like to know.
