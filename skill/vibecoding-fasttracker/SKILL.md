---
name: vibecoding-fasttracker
description: Produce the handover pack that takes a complete beginner to autonomy in vibe coding: the context, the method frame, the roles and the flight plan that their AI will read in order to take over the steering. Trigger when a project is being handed to someone who is starting out and will run it with their own AI (ChatGPT, Claude, anything else): "I'm handing this project over", "handover", "vibe coding coaching", "they'll pick it up with their ChatGPT", "prepare the handover". Do not trigger to start a fresh project between people who already know the trade; that is `project-kickoff`.
---

# Vibecoding Fasttracker

## What you produce, and for whom

A **handover pack**: a folder of documents, inside the project's repository, that lets **the
recipient's AI** take over the steering of the project rather than only the writing of code.

🔴 **The two ends of the chain are never confused.**

| | Who | Reads what |
|---|---|---|
| **The coach** | reads you | this skill |
| **The recipient** | is starting from nothing | the pack's `README.md`, and nothing else at first |
| **The recipient's AI** | ChatGPT, Claude, anything else | all the rest of the pack |

So you are writing for **three different readers** in the same folder. A document that addresses the
wrong one has failed: the recipient's `README.md` is not allowed to be dense, and the technical
brief is not allowed to be pedagogical.

## 🔴 The anti-divergence rule

**This skill contains no method text.** It says which document to fill in and what makes it good,
never what the document says. The `templates/` directory of the `vibecoding-fasttracker` repository
is the single source of everything fixed.

If you catch yourself writing a phrase here that belongs in a deliverable, stop: it goes in the
template, and the template is cited rather than copied.

The same outwards: for the **project method** as a whole (Definition of Ready and Done, the
specification that generates the issues, milestones, board) you **point at** the `kickoff`
repository. You do not rewrite it. Two method texts always drift apart.

---

## Step 0: what you must know before writing a line

Never guess these answers. Ask for them, all at once, and mark `⚠️ À TRANCHER` (to be decided) in the
deliverable for whatever stays open rather than inventing it.

1. **Who is receiving**: their trade, their real level on each tool involved (not "beginner" as a
   block, but beginner at what exactly), their machine, what they want to do themselves and what
   they want to delegate.
2. **Which AI** they will use, and in what form: an assistant configured once and for all, a project
   space, a prompt to paste again each time. The mechanism changes the shape of the deliverable.
3. **Does that AI have repository access?** Almost always no for the steering AI, often yes for the
   coding one. It is the single most structuring question of the pack: an AI without Git access has
   to **ask** for the repository's state rather than assume it, and that has to be written into its
   instructions.
4. **The project**: what already exists, what is being rebuilt, what is being added. And if it is a
   rebuild, **why rebuild rather than evolve**.
5. **The scope beyond the first project.** There usually is one, and it usually goes unsaid.
6. **The paid tools**, who pays, and **on whose account** they live. If the coach's: which access
   they delegate, and what stays with them.
7. **The dependencies** only the coach can clear: access, invitations, accounts.
8. **Where the specification, the progress and the decisions land**, and whether the repository is
   private.

### The three questions nobody remembers to ask

- **"Why rebuild something that works?"** A rebuild decision with no written justification gets
  re-argued at every difficulty, and a project that gets re-argued is a project that stops. If
  nobody can answer, that is an `⚠️ À TRANCHER` at the top of the context, never a justification you
  invent.
- **"What was the old foundation giving away for free?"** Changing stack makes invisible guarantees
  disappear: security carried by the infrastructure, backups, database constraints. Whatever
  disappears has to be listed and reimplemented by name. It is the number one regression risk of a
  rebuild, and it does not show up in the requirements.
- **"Where do the users work?"** Geography and hardware are not local colour: an unstable network,
  modest devices, language, currency and time zone translate into verifiable constraints on the
  code. If they are not written down, they will be forgotten.

---

## Step 1: where the pack goes

**In the project's repository**, under a dedicated folder, rather than in a separate notes space.
The recipient already has the repository cloned in their tool; they receive updates through a sync
they already know how to do, and they can see what changed.

There is one reason to do otherwise: the recipient has no repository at all. In that case pick a
medium they can open without installing anything, and say so explicitly in the pack.

Before writing, check what the repository **already** carries: specification, data model, business
rules. You do not rewrite those, you point at them. What you produce is what is missing: the method,
the roles, the flight plan, and one consolidated reading of the business for the AI's use.

## Step 2: the six deliverables

Each has its template in `templates/`. Fill in, adapt, delete what does not apply, but do not change
the order or the split: it exists so that a lost recipient can always find where they are.

| # | Deliverable | Reader | What makes it good |
|---|---|---|---|
| 1 | **Getting started** (`README.md`) | the recipient, alone | They can go from nothing to "my AI has taken over" with no help and no terminal. Every action names the page, the exact button, and **what they should see at the end** to know it worked |
| 2 | **Method and roles** | the steering AI | Contains the instruction text **ready to paste**, with not a word to adapt. The roles in it are exclusive: who codes, who steers, who decides |
| 3 | **Phasing and checklist** | the steering AI, and the recipient to keep their bearings | Every step has an **exit gate** the recipient crosses explicitly. Ends with a checklist to tick |
| 4 | **Context** | the AI, before any decision | Consolidates what is **already settled** so that it stops being asked again. Separates cleanly what must not change from what is open |
| 5 | **Stack and technical decisions** | the coding AI | Prescriptive rather than descriptive. Every known trap of the existing system is translated into a rule that is verifiable in the new stack |
| 6 | **Presentation page** (HTML) | the recipient, and whoever they want to show | Opens on a double-click, with no login. Objectives, dependencies, phasing, tools and their cost, at a glance |

### Requirements gathering belongs to the steering AI

It is the responsibility people most often forget to write down, and its absence is what turns
coaching into an order-taking workshop. The recipient knows their trade, not how to turn it into a
specification: the steering AI is the one that draws it out of them. The pack has to require of it:

1. **Get them talking about the work, not the screen they imagined.** Who does what, when, with what
   today, and what actually gets stuck.
2. **Simple questions, one at a time**, in plain language. A ten-point questionnaire in one go makes
   a beginner disengage, and a beginner who disengages often does not dare say so.
3. **Reformulate and have it confirmed before writing.** A misunderstood need costs ten times more
   once it is in code.
4. **Then write it** as a story (role, action, benefit) with acceptance criteria that are
   **demonstrable on screen**, an identifier and a priority. Anything that cannot be demonstrated is
   not a story.
5. **Have each story validated by the recipient, in their own words**, before it enters the backlog.

### Where the steering deliverables land

Three places, three uses. The pack has to name them and say **which one is authoritative**, without
which the specification ends up copied in three places that drift.

| Place | What it carries | Authoritative |
|---|---|---|
| The repository (`docs/`) | the specification and the stories, as files | 🔴 yes |
| The tracking board (GitHub Project or equivalent) | progress: one card per story, **derived** from the files | no, it regenerates |
| The wiki | what a human comes to read outside the code: decisions and their reasons, procedures | for its own subject only |

**The repository is private by default**, and making it public is the coach's decision rather than a
side effect. Write that down: a beginner exploring a repository's settings can publish it without
grasping what that exposes.

⚠️ **Who actually creates** the cards and the wiki pages is not obvious: the steering AI has no
access, the coding AI cannot always call an API, and the recipient is not always allowed. Settle it
explicitly in the pack, or mark it `⚠️ À TRANCHER`.

### The accounts stay with the coach, so grant access rather than acting as a relay

Hosting, repository and billing almost always live on the coach's accounts. The natural instinct is
to turn that into a standing request ritual, and **that is a trap**. A setup where every deployment
goes through a human round trip stops at the first slow reply, and never produces autonomy.

The right shape: the coach **grants access once**, as a collaborator on the hosting and on the
repository, and the recipient is autonomous afterwards. All that stays with the coach is the initial
grant, anything touching billing, and the switch to public.

For those few requests, the pack requires the steering AI to **draft the message ready to send**,
never to leave the recipient improvising. Always the same four points: what is being asked, in one
sentence; why now; what is blocked meanwhile; and what the recipient should receive back to know it
is done. And immediately after: **what they can get on with while waiting**.

### What the pack must contain, whatever the project

- **Two AI roles, never confused.** The one that codes does not arbitrate the method; the one that
  steers never touches the code and never claims to have run anything.
- **A fixed step format** for the steering AI, restated before each step: the frame, the
  deliverables, what is expected of it and of the recipient, the prerequisites, what the recipient
  approves, the tools, the next step. No step starts without explicit approval.
- **The steering AI's double role**: guarantor of the solution *and* mentor. The second is the one
  people forget, and it is the one that produces autonomy rather than dependence.
- **One batch open at a time**, with the next thing named in advance. Naming it in advance heads off
  "could we just add this?" mid-project.
- **The cost of the tools stated before** the recipient commits.
- **The dependencies** only they, or only the coach, can clear.

---

## Step 3: what makes a pack bad

Read yourself against this list before handing back. These are observed defects, not hypotheses.

- **A terminal command in a recipient-facing deliverable.** If they do not code, they do not open a
  terminal. Ever. Rewrite it as interface actions, or have the coding AI run it.
- **Jargon left unexplained at its first appearance.** An unexplained word is a word that blocks,
  and a beginner who is blocked often does not dare say so.
- **A deliverable that copies what already exists elsewhere in the repository.** Two truths that
  will drift. Point rather than copy, and when a consolidation genuinely helps, say at the top which
  one wins in a contradiction.
- **A condescending tone.** The recipient is almost always an expert in their own trade and a
  beginner only at the tool. Warm, never paternalistic.
- **An invented justification** because the real one was missing. Mark `⚠️ À TRANCHER` and name who
  has to decide.
- **Phasing with no exit gates.** A list of steps with no passing criterion is not a plan, it is an
  intention.
- **An AI left believing it can see the repository.** It will invent its state with total
  confidence.
- **A setup where the coach stays on the critical path.** If they have to be asked in order to
  deploy, the project stops at the first slow reply. They grant access; they are not a relay.
- **A specification copied into the wiki, or typed into the tracking board first.** Two truths that
  will drift. The file is authoritative and the rest derives from it.

## Step 4: handing back

1. Read each deliverable **as its reader**, in particular the `README.md` as the recipient: can they
   get to the end alone, on a Friday evening, with nobody to ask?
2. List for the coach every `⚠️ À TRANCHER` and every dependency they have to clear themselves.
3. Commit into the project's repository, subject first, then the detail.
4. Add the case to `examples/` in the `vibecoding-fasttracker` repository, **as a pointer, never as
   a copy**, and write down what the case taught the template. That is what makes the Fasttracker
   better from one handover to the next.
5. Write the project's long memory wherever that project keeps it, outside the repository.
