# Vibecoding Fasttracker

*[Version française](README.fr.md)*

Take a complete beginner to **autonomy in vibe coding**, in such a way that their AI takes over the
**steering** of a project, rather than only the writing of code.

This repository is not an application. It is a template: it produces a **handover pack** that you
give to someone who is starting out, and that their AI reads in order to hold the frame in your
place.

---

## The presentation

A standalone page introducing the approach to someone who might adopt it:
[`presentation.html`](presentation.html). It opens in a browser, with nothing to install.

## The problem

Coaching someone through vibe coding always fails at the same point. The code gets handed over and
the method does not. The beginner's AI then writes whatever it is asked for: no frame, no way out,
no finite scope. The project sprawls, then stops.

The Fasttracker hands over both.

## The principle

**Two AIs, two roles, never confused.**

| | The AI that writes code | The AI that steers |
|---|---|---|
| Does | writes and runs the code, in the repository | frames, designs, reviews, holds the method |
| Does not | decide the method | ever touch the code |

**A fixed step format.** Before each step, the steering AI restates, in this order: the frame of the
step, the deliverables, what is expected of it and of the recipient, the prerequisites, what the
recipient has to approve, the tools involved, and the next step. **No step starts until the previous
one has been explicitly approved.**

**A double role for the steering AI.** Guarantor of the solution: architect, QA, keeper of the method
and of the ways out. And mentor: it brings the recipient up to speed on what they need to understand
to stay in charge, without ever drowning them in jargon.

**One batch open at a time.** That is the rule that protects a project from becoming a building site
that never finishes.

---

## The two ends of the chain

🔴 Never confuse them. That mistake produces a pack that addresses the wrong person.

| | Who | With what |
|---|---|---|
| **Who prepares** the handover | the coach | the **Claude skill** in this repository |
| **Who receives** the handover | the beginner | **their own AI**: ChatGPT, Claude, anything else |

## What is in this repository

| Directory | Contents |
|---|---|
| `templates/` | The deliverable templates, with their placeholders. **The source of everything fixed** |
| `skill/vibecoding-fasttracker/` | The Claude skill: the judgement (what to fill in, what makes a deliverable good), never the fixed text |
| `examples/` | Real cases, as pointers to their own repository |

---

## Getting started, on the coach's side

1. Install the skill into your Claude Code configuration:

```bash
cp -R skill/vibecoding-fasttracker ~/.claude/skills/
```

2. Open a Claude Code session in the repository you are handing over, and invoke the skill:

```
/vibecoding-fasttracker
```

3. It asks you what it cannot guess: who is receiving, which project, which AI on their side, which
   tools. Then it produces the handover pack in `docs/refonte/`, or whichever directory you name.

4. Read it, fill in whatever it marked `⚠️ À TRANCHER` (to be decided), commit, and give the
   recipient the repository address. Their entry point is the pack's own `README.md`.

🔴 **The skill is edited here, never in `~/.claude/skills/`.** That directory is an install, and a
change made there is lost on the next copy.

## Getting started, on the recipient's side

The recipient **never** opens a terminal. For every action, the pack they receive gives them the page
to go to, the exact button to click, and what they should see at the end to know it worked. They
start with the pack's `README.md` and read nothing else until they are done.

---

## Where it sits next to `kickoff`

🔴 **The two do not overlap.** Never apply both to the same repository without deciding explicitly:
they would write the same subjects under different file names.

| | [`kickoff`](https://github.com/romain-nicod/kickoff) | Vibecoding Fasttracker |
|---|---|---|
| Who it is for | someone who already knows how to run a project | someone starting from nothing |
| What it installs | the method, in a repository: DoR and DoD, spec to issues, milestones, board | the handover to a third-party AI, and the human's climb up the learning curve |
| What it assumes | terminal, Git, GitHub | nothing |

The Fasttracker **points at** `kickoff` for the project method as a whole. It does not rewrite its
Definition of Done and does not redefine its milestones. A method rule that changes, changes there.

## A note on language

The deliverable templates in `templates/` are written in French, because they are read by the
recipient rather than by a developer, and the first cases were French-speaking. The method around
them is here in English. Translating a template is a matter of translating one file: the skill fills
in whatever it is given.

## Licence

[CC BY 4.0](LICENSE). Reuse it, adapt it, sell what you build with it. Keep
the credit visible, as [`NOTICE`](NOTICE) explains.
