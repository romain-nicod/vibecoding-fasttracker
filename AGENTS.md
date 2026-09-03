# AGENTS.md — vibecoding-fasttracker

> 🔴 **The long memory of this repository lives outside it.** Decisions and their reasons, traps
> already paid for, state of play: they belong in a notes folder that survives the code. This file
> carries only the rules for working on this repository.

## What this repository is

A template for **taking a complete beginner to autonomy in vibe coding**. It produces a handover
pack: what to give the recipient's AI so that it takes over the steering of a project, and what to
give the recipient so that they can install all of it without understanding the technical side.

First real case: handing a management application over to its director (`examples/`).

## The two ends of the chain, never to be confused

| | Who | Tool |
|---|---|---|
| **Who prepares** the handover | the coach | the Claude skill in this repository |
| **Who receives** the handover | the beginner | their own AI: ChatGPT, Claude, anything else |

The skill in this repository is a **Claude skill**. What it produces can target any AI. Confusing
the two produces a skill that addresses the wrong person.

## 🔴 The absolute rules

1. **The skill contains no method text.** It says which document to fill in and what makes it good,
   never what the document says. `templates/` is the single source of everything fixed. It is the
   same anti-divergence rule as in `kickoff`, for the same reason: two method texts always drift
   apart.
2. **This repository does not rewrite `kickoff`'s method.** Definition of Ready and Done, spec to
   issues, milestones, board: that lives in `romain-nicod/kickoff`, and this one points at it. A
   method rule that changes, changes there.
3. **No client name in `templates/` or in `skill/`.** A template carrying one client's business is
   no longer a template. Real cases live in `examples/`, as pointers only, never as copies.
4. **The recipient never opens a terminal.** Everything the templates ask of them happens in a web
   interface or an application, with the page, the button, and what they should see at the end. A
   shell command in a recipient-facing deliverable is a bug.
5. **One batch open at a time** is the rule this whole approach protects. Any template that allows
   two work streams to open in parallel needs fixing.

## Structure

| Directory | Contents |
|---|---|
| `templates/` | The deliverable templates, with their placeholders. The source of everything fixed |
| `skill/vibecoding-fasttracker/` | The Claude skill: the judgement, never the fixed text. Installed by copying into `~/.claude/skills/`. **Edit it here, never there** |
| `examples/` | Real cases, as pointers to their own repository. Never a copy |

## Language

**English for everything that describes the method**: this file, the README, the skill, commit
messages.

**The deliverable templates exist in both languages**, in `templates/en/` and `templates/fr/`. They
are read by the handover recipient rather than by a developer, so the pack is produced in whichever
language that person reads.

The two sets are independent, placeholder names included: `{{RECIPIENT}}` on one side,
`{{DESTINATAIRE}}` on the other. Never mix them inside one pack. A new language is a new directory,
never a replacement of an existing one.

File and directory names stay in ASCII `kebab-case`.
