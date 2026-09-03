# Template — Phasing and checklist (deliverable 3)

> **This template becomes `01-phasing-and-checklist.md` in `{{PACK_DIR}}`.**
> It has **two readers**: the steering AI, which uses it as a map to frame each step, and the
> recipient, who uses it to find their bearings: where things stand, what is left, and what is **not**
> being done now.
>
> 🔴 **A step with no exit gate is not a step.** A list of steps with no passing criterion is not a
> plan, it is an intention. Each exit gate is phrased as **an action the recipient performs themselves
> and whose result they see on screen**, never as a code review, never as a "looks good".
>
> 🔴 **No terminal commands here.** The recipient never opens one. Everything asked of them happens in
> a web page or an application, with the button and what they should see at the end.
>
> 🔴 **Do not rewrite the project method.** Ready and Done, the specification that generates the
> backlog, milestones and board live in `{{METHOD_REPO}}`. This **points** at them, rather than copying
> them.

## This template's placeholders

🔴 **This section is removed from the produced deliverable.**

| Placeholder | What it stands for | Example |
|---|---|---|
| `{{PROJECT}}` | the project's or application's name | `Workshop Invoicing` |
| `{{ORGANISATION}}` | the recipient's company or organisation | `the workshop` |
| `{{RECIPIENT}}` | first name of the person receiving the handover, who will steer | `Camille` |
| `{{COACH}}` | first name of the person handing over | `Alex` |
| `{{COPILOT_NAME}}` | the name given to the steering AI | `Workshop Copilot` |
| `{{STEERING_AI}}` | the form that AI takes: configured assistant, project space, prompt | `a configured assistant` |
| `{{CODING_AI}}` | the tool that writes and runs the code | `Codex` |
| `{{AI_PLAN}}` | the paid plan giving access to both AIs | `ChatGPT Pro` |
| `{{REPO}}` | the repository's short path | `my-org/workshop-invoicing` |
| `{{REPO_URL}}` | the repository's full web address | `https://github.com/my-org/workshop-invoicing` |
| `{{REPO_HOST}}` | where the repository is hosted | `GitHub` |
| `{{PACK_DIR}}` | the repository directory holding this handover pack | `docs/handover/` |
| `{{DOMAIN_DOCS_DIR}}` | the directory or directories already holding the domain documentation | `docs/product/` and `docs/specs/` |
| `{{SPEC_DIR}}` | the directory where the specification and stories land, **the authoritative one** | `docs/specs/` |
| `{{TRACKING_BOARD}}` | the tool carrying progress, one card per story | `the repository's Projects board` |
| `{{WIKI}}` | where a human goes to read decisions and procedures, outside the code | `the repository wiki` |
| `{{METHOD_REPO}}` | the method template repository being pointed at | `my-org/kickoff` |
| `{{HOSTING}}` | where the application goes live, on the coach's account | `Fly.io` |
| `{{HOSTING_COST}}` | what the hosting costs per month, once live | `~$8/month` |
| `{{LOCAL_CURRENCY}}` | the currency the recipient thinks in day to day | `euros` |
| `{{STACK}}` | the target stack, as a short phrase | `Laravel + MySQL` |
| `{{CURRENT_STACK}}` | what runs the application today | `a no-code generator and its hosted database` |
| `{{DIAGRAM_TOOL}}` | the sketching and mockup tool the recipient handles | `Excalidraw` |
| `{{MODULE_LIST}}` | the functional modules, **in order of value**, comma-separated | `files, workers, jobs, scheduling, dashboard` |
| `{{PIVOT_MODULE}}` | the module carrying the core of the business, and the heaviest | `jobs` |
| `{{ADMIN_ROLE}}` | the role that sees and can do everything | `administrator` |
| `{{RESTRICTED_ROLE}}` | the limited role, the one the regression check targets | `field worker` |
| `{{SENSITIVE_DATA}}` | what `{{RESTRICTED_ROLE}}` must see **nowhere** | `pay data` |
| `{{TARGET_DEVICE}}` | the device the real validation happens on | `your phone` |
| `{{DATA_VOLUME}}` | what there is to migrate, in real volume | `around 200 files, 40 workers and three years of history` |
| `{{FALLBACK_PERIOD}}` | how long the old application stays reachable as a fallback | `2 months` |
| `{{FIRST_NEW_FEATURE}}` | the first genuinely new feature, named in advance | `sending the weekly summary automatically` |
| `{{VERSION}}` | the document's version | `v01` |
| `{{DATE}}` | the date it was last changed | `25/08/2026` |

---
---

# {{PROJECT}} — the flight plan

*This preamble says who the document is for and how it is used. It has to fit on one screen: a
recipient opening this file for the first time must not feel they are facing a wall of text to read
end to end.*

This document is the **flight plan**: the steps in order, what each produces, and the **exit gate** you
cross explicitly before moving to the next. It does not replace {{COPILOT_NAME}}, it serves as its map:
at every new conversation you can say "we're at step 5, open it" and it will know exactly what to
frame. You use it to find your bearings: where things stand, what is left, and what we will **not** be
doing now.

You do not have to read it end to end today. Read the preamble, look at the diagram below, then open
only the section for the current step. The checklist at the end gives you your progress at a glance.

> **Prerequisite**: the getting started described in `{{PACK_DIR}}`'s `README.md` is done: repository
> access, {{CODING_AI}} synced, {{COPILOT_NAME}} created, {{DIAGRAM_TOOL}} ready. That is step 1 below,
> and this document picks up right after.

---

## The non-negotiable rules

*Three rules, never more. They are what holds the rest of the document together: every step is only
their application at a particular moment. If you add a fourth, check that it is not a consequence of
one of the three. A list of rules nobody remembers protects nothing.*

**1. One batch open at a time.** Never two work streams in parallel. If a good idea comes up in the
middle of a step, {{COPILOT_NAME}} notes it in a "later" list and it is not touched. This is the rule
that stops a project spreading out indefinitely.

**2. We finish like for like before adding anything new.** *Like for like* means: the new application
does **exactly** what the current one does, no more and no less. No new feature enters before step 11.
The first of them is already known: {{FIRST_NEW_FEATURE}}. It waits its turn.

**3. A step does not open while the previous one has not been approved by you, explicitly.** Not
"looks fine": an "I approve step N" written into the conversation with {{COPILOT_NAME}}. That is what
keeps you in charge.

---

## Overview

*The diagram below is a **generic skeleton**: replace the labels in angle brackets with the project's,
and nothing else.*

🔴 **Three rules so as not to break it:**

1. **Fixed width.** Each label has to fit its cell without overflowing or shortening it. If a module
   name is too long, abbreviate it in the diagram. The full name lives in that step's section.
2. **No double-width characters.** No emoji, no ideograph, no exotic symbol inside the block: they take
   two columns when displayed and shift the whole frame. Latin accents cause no problem.
3. **A diagram that lies is worse than no diagram.** If you add or remove a step, the block gets
   redrawn. It is not allowed to drift.

```text
 ┌────────────────────────┐    ┌────────────────────────┐    ┌────────────────────────┐
 │ 1  Getting started     │    │ 5  Technical base      │    │ 8  The screens         │
 │    tools, access,      │    │    + an EMPTY page     │    │    a. <module 1>       │
 │    steering AI created │    │      already LIVE      │    │    b. <module 2>       │
 ├────────────────────────┤    ├────────────────────────┤    │    c. <PIVOT MODULE>   │
 │ 2  Framing             │    │ 6  Data structure      │    │    d. <module 4>       │
 │    scope frozen        │──► │                        │──► │    e. <module 5>       │
 │    budget stated       │    │    traps carried over  │    │    f. <module 6>       │
 ├────────────────────────┤    ├────────────────────────┤    ├────────────────────────┤
 │ 3  Repo and method     │    │ 7  Sign-in and rights  │    │ 9  Migrating the       │
 │    needs gathered      │    │    what the old base   │    │    real data           │
 │    backlog derived     │    │    provided for free   │    │    nothing lost        │
 ├────────────────────────┤    └────────────────────────┘    └────────────┬───────────┘
 │ 4  Hosting access      │                                               │
 │    granted once by     │                                               │
 │    the coach           │                                               │
 └────────────────────────┘                                               │
                              ┌───────────────────────────────────────────┘
                              ▼
             ┌────────────────┴────────────────┐
             │ 10 Acceptance and switchover    │
             │    the old one stays as backup  │
             │    <fallback period>            │
             └────────────────┬────────────────┘
                              │
             ═══════ END OF THE REBUILD ══════
                              │
                              ▼
             ┌────────────────┴────────────────┐
             │ 11 <1st new feature>            │
             │    named in advance             │
             │    never before                 │
             └─────────────────────────────────┘

 FIXED ORDER — it cannot be reversed              FREE ORDER — you choose
 ───────────────────────────────────────────      ───────────────────────────
 1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9 → 10 → 11      · the order of step 8's
 Each step needs the previous one's result.         modules, after the pivot
 Skipping means redoing it later.                   module
 The one exception: step 4, purely               · the pace: one step a week or
 administrative, can run during step 3.             a month, it changes nothing
                                                    about the method
```

**What this diagram tells you**: nothing that produces visible value (right-hand column) arrives before
the foundation holds (middle column). That is deliberate. An application with beautiful screens that
nobody knows how to bring back online after an outage is not deliverable.

And one note on duration: in step 8, the **{{PIVOT_MODULE}}** module weighs as much on its own as all
the others put together. If you feel the project is grinding at that point, that is normal: it is the
core of the business being rebuilt.

---

## Step 1 — Getting started

*This step exists for one reason: without it, every later step waits. It produces nothing visible, and
that is exactly why it is treated as a step in its own right with its own exit gate. Otherwise it gets
believed to be done while an access is missing. Its step-by-step detail lives in `{{PACK_DIR}}`'s
`README.md`; here we keep only the reminder and the gate.*

**Objective**: that {{RECIPIENT}} has their tools in hand and {{COPILOT_NAME}} in place, before a
single project decision is taken.

### Deliverables

| Deliverable | What it is |
|---|---|
| **Access to the {{REPO}} repository** | The invitation accepted, the repository visible in their {{REPO_HOST}} account |
| **{{CODING_AI}} synced** | It can see the repository and knows how to write to it |
| **{{COPILOT_NAME}} created** | {{STEERING_AI}}, configured with the text from `00-method-and-roles.md` |
| **{{DIAGRAM_TOOL}} open** | The account created, a test sketch made and found again |

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COACH}}** | Invites {{RECIPIENT}} onto {{REPO}} and hands over the pack |
| **{{COPILOT_NAME}}** | Does not exist yet: it is this step's output |
| **{{CODING_AI}}** | Connects to the repository |
| **You** | You follow the folder's `README.md`, screen by screen |

### 🚪 Exit gate

You open a conversation with {{COPILOT_NAME}}, you write "we're starting {{PROJECT}}, frame step 2 for
me", and **it answers respecting the step format**: the frame, the deliverables, who does what, what
you will have to approve. If it answers anything else, its configuration is incomplete: go back to the
`README.md`.

### Known traps

- **An accepted access is not a verified access.** Open the repository in your browser and see it with
  your own eyes before ticking.
- {{COPILOT_NAME}} does not resync itself with the repository. Every time a file in `{{PACK_DIR}}`
  changes, it has to be given the current version again, otherwise it works on stale material without
  telling you.

---

## Step 2 — Framing

*This is the step that decides the length of the whole project. Three things get frozen: what we do,
what we do not do, and what it costs. The "what we do not do" section is the one people always skip,
and it is the one that helps most: with no written "later" list, every good idea re-argues the scope.*

**Objective**: to freeze in black and white what is being rebuilt, what is not, and what it will cost
in subscriptions, before a single line of code is written.

### Deliverables

| Deliverable | What it is | Where it lives |
|---|---|---|
| **Framing note** | 2 pages: the scope, what is explicitly excluded, the target date | {{COPILOT_NAME}} produces it; its final version goes into `{{SPEC_DIR}}` |
| **Tools budget** | A table: each tool, its monthly cost, its annual equivalent in {{LOCAL_CURRENCY}} | In the framing note |
| **"Later" list** | Everything refused for now, so it does not get reinvented three times | In the framing note, its own section |

### What is already settled, do not re-argue it

*Point here at the context deliverable, and name it. The goal is that a decision already taken is never
questioned again by the AI, which is what wears a beginner out faster than anything else.*

The `02-context.md` file in this folder holds all the business that has already been settled: data
structure, business rules, each role's permissions, definitions of the figures. **Those decisions are
authoritative.** {{COPILOT_NAME}} must not ask you for them again; if you see it doing so, send it back
to the document, because it has probably lost the thread.

So the scope is simple to state: **everything {{ORGANISATION}}'s current application does, and nothing
more.** What was already deferred stays deferred.

### The budget to state

*The cost is stated **before** the commitment, and **even when the recipient is not the one paying**:
it is not their wallet at stake, it is their decision. Give a dated order of magnitude and say it is to
be rechecked. An undated figure will be quoted as a promise in six months.*

🔴 **The {{HOSTING}} hosting is on {{COACH}}'s account, not yours.** You open no account, you hand over
no card, and you will never be asked to. The table below tells you what it costs anyway: a cost nobody
states is a cost that will surprise you one day.

| Tool | What it does | Cost | Who pays |
|---|---|---|---|
| **{{HOSTING}}** | Runs the application and stores the data | {{HOSTING_COST}} | **{{COACH}}**: their account, their invoice |
| **{{AI_PLAN}}** | {{CODING_AI}} and {{COPILOT_NAME}} | already paid | you, already running |
| {{REPO_HOST}} | Hosts the code | free at this usage | — |
| {{DIAGRAM_TOOL}} | The sketches and mockups | free | — |
| **New total** | | **{{HOSTING_COST}}** | **nothing new charged to you** |

⚠️ That it is {{COACH}}'s invoice does not mean we let it drift. The classic trap is forgetting a test
environment left running for two months. Only one will be created, and step 4 shows you where to see
the usage.

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COPILOT_NAME}}** | Writes the framing note, prices the budget, opens the "later" list |
| **{{CODING_AI}}** | Nothing. No code is touched at this step |
| **You** | You read, you challenge what looks wrong, you approve |

### 🚪 Exit gate

You write to {{COPILOT_NAME}} that **you approve the framing note**, confirming three things:

1. The scope really is "everything the current application does, nothing more".
2. You have seen what the hosting costs ({{HOSTING_COST}}, on {{COACH}}'s account) and you know
   nothing new is charged to you.
3. You have seen the "later" list and you agree that nothing comes out of it before step 11.

### Known traps

- **The whole project's number one trap**: "while we're at it, we could also…". Every addition at this
  stage looks tiny and costs three weeks. Everything that comes up goes into the "later" list, without
  exception, your own ideas included.
- A rebuild where nobody can say **why** we are rebuilding rather than evolving gets re-argued at every
  difficulty. If the reason is written nowhere, that is a `⚠️ TO BE DECIDED`, not a justification
  {{COPILOT_NAME}} invents.

---

## Step 3 — Preparing the repository and the method

*The densest step of the plan, and the one people are most tempted to skim. It lays down three things
at once: **who gathers the requirements**, **the three destinations for the work**, and **the fact that
the repository is private by default**. All three are operating rules rather than tasks: once laid
down, they govern the rest of the project.*

**Objective**: to give the project its backbone, the method documents and a task list derived from a
written specification rather than reinvented in a meeting.

### Who gathers the requirements, and how it goes

*This is the responsibility people most often forget to write down, and its absence turns coaching into
an order-taking workshop. Write it here even if it seems obvious.*

🔴 **{{COPILOT_NAME}} is the one that draws the specification out, never you writing it.** You know
your trade; how to turn it into work items is its business. Concretely, it has to:

1. Get you talking about **your work**, not the screen you imagine: who does what, when, with what
   today, and what actually gets stuck.
2. Ask **simple questions, one at a time**, in plain language. A ten-point questionnaire in one go and
   you disengage, and nobody will know.
3. **Play it back and have you confirm before writing** anything.
4. Then write it as a story (role, action, benefit) with criteria that are **demonstrable on screen**,
   an identifier and a priority.
5. Have you **approve each story in your own words**. If you cannot say it back, it is not understood:
   back to point 3.

### Three places, three uses, never to be mixed

*This is the rule that avoids the worst failing of this kind of project: the same information in two
places, ending up saying two different things without anyone noticing. Name the three places and say
which one is authoritative.*

| Place | What it carries | Authoritative |
|---|---|---|
| **The repository**, `{{SPEC_DIR}}` | the specification and the stories, as files | 🔴 **yes** |
| **{{TRACKING_BOARD}}** | progress: one card per story, **derived** from the files | no, it regenerates |
| **{{WIKI}}** | decisions and their reasons, procedures, how-tos | for its own subject only |

- A {{TRACKING_BOARD}} card is **never typed by hand first**. If a card contradicts a file, **the file
  wins** and the card is regenerated.
- **Never a duplicate specification in {{WIKI}}.** It carries the why and the how, not the what.
- 🔴 **The {{REPO}} repository is private by default.** Making it public is {{COACH}}'s decision, never
  a side effect: a beginner exploring a repository's settings can publish it without grasping what
  that exposes.

⚠️ **TO BE DECIDED if it has not been already: who actually creates** the cards and the {{WIKI}} pages?
{{COPILOT_NAME}} has no access, {{CODING_AI}} cannot always call an API, and you do not always have the
rights. Name who performs the action, tool by tool.

### Deliverables

| Deliverable | What it is |
|---|---|
| **Method documents** in the repository | Imported from `{{METHOD_REPO}}`, **not rewritten** |
| **The framing note in the project's format** | The one from step 2, filed in `{{SPEC_DIR}}` |
| **Generated backlog** | The work items, derived from `{{DOMAIN_DOCS_DIR}}` |
| **{{TRACKING_BOARD}}** | The progress board, one card per story |
| **{{WIKI}} enabled** | Empty at first. It fills up with decisions and procedures |
| **Milestones** | One milestone per step 5 to 10 of this document, to see the progress |

### The method's two gates

*Do not rewrite them here.* "Ready" and "Done" are defined in `{{METHOD_REPO}}`, which is
authoritative. {{COPILOT_NAME}}'s role at this step is to **explain them to you in plain language**,
once, with an example drawn from your own trade, and then to hold them. Your role is to ask it "is that
done by the definition?" every time it tells you a task is finished.

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COPILOT_NAME}}** | Leads the requirements gathering, writes the stories, prepares the documents' content, reviews the generated backlog and flags the gaps |
| **{{CODING_AI}}** | Imports the method documents and runs the item generation |
| **{{COACH}}** | Grants the access; creates {{TRACKING_BOARD}} and enables {{WIKI}} while you do not have the rights. The repository stays **private** |
| **You** | You answer the questions about your trade, you approve each story in your own words, you read through the item list |

### 🚪 Exit gate

Two things, together:

1. You open [{{REPO_URL}}]({{REPO_URL}}) in your browser and you see **a list of labelled items,
   grouped by module**. You go through it and tell {{COPILOT_NAME}} "I approve the backlog", or you
   point out what is missing.
2. You can say, **without rereading this document**, where the specification, the progress and the
   decisions live: the three places, and which one is authoritative.

### Known traps

- **The backlog is not typed into {{TRACKING_BOARD}}.** It is written in `{{SPEC_DIR}}`, and the board
  follows from it. A card created by hand is information that exists nowhere else: it will be lost at
  the first regeneration.
- **{{WIKI}} is not a second requirements document.** As soon as you see a specification copied into
  it, say so: there are now two truths, and one of them is already wrong.
- The repository already holds the current application. **It does not get erased**: it stays live and
  serves as the reference until step 10. Where to put the new code without overwriting the existing is
  a decision to take explicitly here, not to improvise.

---

## Step 4 — Hosting access

*The most administrative step, the only one depending on an action by the coach, and the one where the
whole setup's autonomy is decided. Write it as a **one-off grant**, never as a request ritual: if every
deployment goes back through the coach, the project stops at the first slow reply.*

**Objective**: that {{CODING_AI}} can deploy, and that **you** have access to the application that will
receive it, without going back through {{COACH}} for day-to-day work.

🔴 **The application lives on {{COACH}}'s {{HOSTING}} account, not yours.** You open no account, you
hand over no card, and **nobody should ask you to**: not {{COPILOT_NAME}}, not {{CODING_AI}}, not
{{COACH}}. If you are ever asked, that is a mistake: flag it.

What {{COACH}} does, **once**: they create the application on their account and **add you as a
collaborator**. From then on, **you are autonomous**: you deploy, you read the logs, you see the
dashboard.

### Deliverables

| Deliverable | What it is |
|---|---|
| **{{CODING_AI}}'s environment working** | The {{STACK}} stack installed where it works |
| **{{HOSTING}} application created**, empty | Created by {{COACH}} **on their account**, with its exact name noted |
| **Your collaborator access** | The invitation accepted: the application appears in your dashboard |
| **Deployment access for {{CODING_AI}}** | The key wired into its configuration |

### What you do yourself, step by step

**No terminal command is asked of you**, not here and nowhere in this document. {{CODING_AI}} runs
things; you click in web pages.

**A. Send the request to {{COACH}}.** You do not write this message yourself: **{{COPILOT_NAME}} drafts
it for you, ready to send**, with its four points (what is being asked; why now; what is blocked
meanwhile; what you should receive back). It has to add, straight away, **what you can get on with
while waiting**. A request sent never brings the whole project to a halt.

**B. Accept the invitation.** You get an email from {{HOSTING}} (check your spam, it often lands
there). The link will ask you to create a **free** account, with no card: the card is already
{{COACH}}'s. **What you should see at the end**: the application appears in your dashboard, marked
"collaborator". It is empty, which is normal.

**C. Find the three screens you will actually use**: the application's status, the deployment history
(that is where you will see {{CODING_AI}}'s work arrive), and the logs (that is what you will be asked
to look at the day something stops responding).

**D. Give {{CODING_AI}} the deployment access.** {{COPILOT_NAME}} will guide you when the time comes.
That key is a secret: it is pasted into {{CODING_AI}}'s configuration, **never into a conversation**,
never into a file in the repository.

### What stays with {{COACH}}, even afterwards

| What stays with them | Why |
|---|---|
| Granting access ({{HOSTING}}, {{REPO_HOST}}) | they are their accounts |
| Anything touching the **paid plan** | it is their card |
| Any switch of a **repository to public** | the repository is private by default |

Everything else (deploying, reading the logs, restarting, looking at the dashboard) is yours.

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COACH}}** | Creates the application on **their** account, adds you as a collaborator, sends back the exact name |
| **{{COPILOT_NAME}}** | Drafts the ready-to-send request, guides you screen by screen, tells you what to get on with while waiting |
| **{{CODING_AI}}** | Sets up its environment; wires in the deployment key |
| **You** | You send the request, accept the invitation, and check that you can see the application |

### 🚪 Exit gate

Three things, together:

1. **You can see the application in your {{HOSTING}} dashboard** (it is empty, which is normal), and
   you know where the logs are.
2. You know **the application's exact name** and it is noted somewhere other than in an email.
3. {{CODING_AI}} confirms to {{COPILOT_NAME}} that it can start the application on its side.

### Known traps

- **The standing request ritual.** If you see "ask {{COACH}} before every deployment" written
  somewhere, that is a bug in the setup: check whether it is not already an access granted once and
  for all.
- A test environment left running costs money every month and produces nothing. Only one gets created.
- An access key pasted into a conversation is a compromised key. It gets revoked and reissued. Nobody
  "is more careful next time".

---

## Step 5 — The technical base, and a first empty deployment

*The step that inverts the intuitive order, and that is exactly its point: **"it deploys" before "it
works"**. Explain why, otherwise it looks like a waste of time. A project that deploys for the first
time after three months discovers, at the worst moment, everything that only works on the developer's
machine.*

**Objective**: that an empty page, but **genuinely live**, is reachable from your browser. Nothing
business-related. Just the proof that the whole chain works.

### Why an empty page live, before everything else

Because deployment is where the unpleasant surprises turn up, and we want to find them **now**, while
there is nothing to lose. Once that page is live, every module in step 8 goes live as soon as it is
finished, never accumulated.

### Deliverables

| Deliverable | What it is |
|---|---|
| **The {{STACK}} skeleton** | The project created, in the repository |
| **An empty home page, live** | A web address you can open from {{TARGET_DEVICE}} |
| **The repository's `README.md` up to date** | The live address in its **first few lines** |
| **Automated deployment** | An accepted change goes live with no manual step |

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COPILOT_NAME}}** | Settles the foundation choices from `03-stack-and-technical-decisions.md`, reviews what {{CODING_AI}} produces |
| **{{CODING_AI}}** | Creates the project, deploys it, wires up the automation |
| **You** | You open the address and confirm that you can see the page |

### 🚪 Exit gate

You open the application's address **on {{TARGET_DEVICE}}**, and a page appears: empty, but it appears,
and it appears straight away. You reload it five minutes later: it answers just as fast.

### Known traps

- **"It works on my machine" does not count.** Until it is opened from your own device, at your public
  address, it is not live.
- The foundation decisions listed in `03-stack-and-technical-decisions.md` get settled **now**. Each
  one is expensive to change once data exists.
- The `README.md` carries the live address from its first lines, in **the same change** as the
  deployment, rather than in an end-of-project pass.

---

## Step 6 — The data structure

*The step where the existing system is carried over without being reinvented. Its value rests on one
thing: the list of **the current system's traps translated into verifiable rules** in the new one. A
known trap that is not written here will be reintroduced. That is mechanical.*

**Objective**: to carry the current application's data structure into {{STACK}}, identically, without
reintroducing the traps that took months to understand.

### Deliverables

| Deliverable | What it is |
|---|---|
| **The structure created** | The tables and their links, in the new database |
| **The guardrails** | The checks the database refuses to let through, carried over one by one |
| **The structure document** in `{{DOMAIN_DOCS_DIR}}` | Up to date, read through by you |
| **A test data set** | Enough to fill step 8's screens without touching the real data |

### The traps not to reintroduce

*Carry over here, one line each, the traps listed in `03-stack-and-technical-decisions.md`. Number
them: the exit gate consists of ticking them off one by one, and an unnumbered list cannot be ticked.*

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COPILOT_NAME}}** | Translates each trap into a verifiable rule, reviews the resulting structure |
| **{{CODING_AI}}** | Writes the structure and the guardrails |
| **You** | You read the structure document in plain language and say whether a case from your trade is missing |

### 🚪 Exit gate

{{COPILOT_NAME}} shows you the numbered list of traps and **ticks each one in front of you**, saying
which rule stops it coming back. You confirm that the structure really does describe your trade,
including the awkward cases only you know about.

### Known traps

- **A structure "improved" in passing** is a structure that no longer matches the real data to be
  migrated at step 9. We carry over; we do not improve.
- A guardrail that lives only in the code, and not in the database, falls at the first data import.

---

## Step 7 — Sign-in and permissions

*🔴 **The most underestimated step of the plan, and the number one regression risk.** The old
foundation provided for free things nobody ever wrote into a requirements document: who sees what, who
can do what, what is refused on the server rather than merely hidden on screen. Those guarantees
disappear with it. This step exists to **reimplement them by name**, and the exit gate has to be phrased
as an observed refusal, never as an absent link.*

**Objective**: that everyone can sign in, and that what the old foundation forbade on its own is now
forbidden **explicitly**, by code written for the purpose.

### What gets installed

| Component | What it is for |
|---|---|
| **Sign-in** | Username, password, forgotten password, sign-out |
| **The roles** | {{ADMIN_ROLE}} and {{RESTRICTED_ROLE}}, as defined in `02-context.md` |
| **Authorisation** | Deny **by default**: anything not explicitly allowed is refused |
| **Deactivating an account** | A deactivated account loses access immediately |

### What the old foundation provided, and has to be rewritten

*List here, line by line, what {{CURRENT_STACK}} guaranteed without anyone having to write it, and the
component that replaces it. The full table lives in `03-stack-and-technical-decisions.md`; here we keep
the reminder that stops the step being believed finished too early.*

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COPILOT_NAME}}** | Checks the permissions matrix line by line against `02-context.md`, insists on the refusal tests |
| **{{CODING_AI}}** | Writes the sign-in, the roles, the authorisation and their tests |
| **You** | You try **yourself** to do what you should not be able to do |

### 🚪 Exit gate

The action, and no other: **you sign in with a {{RESTRICTED_ROLE}} account and type directly the
address of a screen reserved for {{ADMIN_ROLE}}.** You must see a **refusal**: not a blank page, not an
absent link. A hidden link is not protection, it is a hidden link.

Then: you ask {{COACH}} or {{COPILOT_NAME}} to deactivate a test account while you are signed in with
it, and you watch the access fall away.

### Known traps

- **Hiding is not forbidding.** A button you cannot see is still reachable by its address.
- {{SENSITIVE_DATA}} must appear **nowhere** for {{RESTRICTED_ROLE}}: not on screen, not in an export,
  not in a search, not in a total that would let it be guessed.
- An authorisation left for "later" never gets caught up: at step 8, every module will add its own
  screens on top.

---

## Step 8 — The screens, one module at a time

*The longest step. What makes it bearable is the split: **each module is a closed batch**, and the
order is functional rather than alphabetical. Say explicitly which module is the heaviest: a recipient
who thinks they are grinding on the pivot module worries for nothing, or worse, pushes the AI to
rush.*

**Objective**: to rebuild the current application's screens, one module at a time, each deployed as
soon as it is finished.

**Each module is a closed batch**: it is opened, finished, approved, then the next one starts. Never
two at once.

### The order, and why

The order of value is: {{MODULE_LIST}}. It is not alphabetical, it is **functional**: each module needs
the previous one, and the module that reads all the others comes last. The **{{PIVOT_MODULE}}** module
is the core of the business, so expect it to weigh as much as all the others put together.

### What every module produces, without exception

| Deliverable | Who produces it | Who approves it |
|---|---|---|
| **Mockup** of the screens in {{DIAGRAM_TOOL}}, with the four states: empty, loading, error, full | {{COPILOT_NAME}} proposes, you adjust | You |
| **The screens**: list, detail, create, edit | {{CODING_AI}} | You, in the live application |
| **The tests**: one per criterion on the item | {{CODING_AI}} | The automated tests |
| **Deployment** of the module | {{CODING_AI}} | You |
| **Journey documentation** updated | {{CODING_AI}} | {{COPILOT_NAME}} |

**The error state is the one nobody ever draws**, and it is the one that breaks during a demo.
{{COPILOT_NAME}} has to get you to approve it explicitly at each module.

### The points to watch, module by module

*One line per module: the business rule people forget, and the permission that applies to it. This is
the section that avoids rediscovering in acceptance testing what the recipient has always known.*

### 🚪 Exit gates

**One per module.** The same action every time: you open the live application **on {{TARGET_DEVICE}}**,
you go through the module's real journey end to end, and you confirm to {{COPILOT_NAME}} "module X
approved". It is not a code review, it is a trial with your own hands.

For {{PIVOT_MODULE}}, the validation journey is fuller: describe it here, step by step, through to the
expected side effect on the other modules.

### Known traps

- **{{TARGET_DEVICE}}, not the developer's computer.** A validation done anywhere other than where the
  work really happens proves nothing.
- {{PIVOT_MODULE}} is the module where the urge to add "just one small thing" is strongest. That is the
  "later" list, always.
- Every finished module goes live. Three do not get accumulated to be delivered together.
- A security review is due at every module touching money or data entry, so nearly all of them.

---

## Step 9 — Migrating the real data

*One rule governs this step, and it overrides all the others: **no real data is lost, and nothing is
recreated from scratch**. The second half matters as much as the first: data retyped by hand is data
nobody can vouch for any more.*

**Objective**: to move the real data into the new application without losing a single record, and
**without papering over** the anomalies it contains.

### What is being moved

{{DATA_VOLUME}}.

### The known anomalies, and the rule governing them

*List here the anomalies already spotted in the current data. The rule: an anomaly is **migrated as
is**, then corrected in the new application, by hand, with a trace. An anomaly "cleaned up" in passing
is a difference in a total that nobody will be able to explain six months later.*

### Deliverables

| Deliverable | What it is |
|---|---|
| **The transfer** | The mechanism that moves the data, replayable |
| **The check report** | How many records went in, how many came out, and the discrepancies |
| **The comparison of totals** | The same figures on both sides |
| **The list of anomalies handled** | What was corrected after migration, and by whom |

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COPILOT_NAME}}** | Defines the checks, insists on the report, refuses an unexplained discrepancy |
| **{{CODING_AI}}** | Writes and runs the transfer, produces the report |
| **You** | You compare the totals and spot-check records you know by heart |

### 🚪 Exit gate

Two actions, both yours:

1. You compare the **totals** between the old and the new application, and they match.
2. You open **five records at random**, including the ones you know are awkward, and you find exactly
   what you know.

### Known traps

- **Data retyped by hand is not migrated data.** If a case resists, we understand why; we do not
  retype it.
- A transfer that cannot be replayed is a transfer nobody will dare rerun. It has to be able to run
  twice without creating duplicates.
- Counters and numbering must restart **after** the last migrated number, never at zero.

---

## Step 10 — Acceptance by you, then switchover

*The only step where the recipient is the sole judge. It runs **in parallel**, the old and the new side
by side on real work, and the old one stays on after the switchover. A switchover with no safety net is
a switchover nobody lets themselves make, which is a rebuild that never ends.*

**Objective**: that you use the new application on your real work, alongside the old one, until nothing
is missing for you, and then that we switch.

### How it goes

1. **In parallel**, over an agreed period: everything you do in the old one, you do again in the new
   one. It is tedious, and it is the price of confidence.
2. You note **everything** that is off, however small, in a single list.
3. {{COPILOT_NAME}} sorts it: blocking, to fix before switchover, or "later" list.
4. We fix the blocking ones, **and only those**.
5. Training the other users, **on {{TARGET_DEVICE}}**, with their own accounts.
6. **A backup actually restored**, at least once, before the switchover. A backup that has never been
   restored is not a backup, it is an intention.
7. Switchover. The old application **stays reachable for {{FALLBACK_PERIOD}}**, read-only, with a
   noted shutdown date.

### Who does what

| Role | What they do at this step |
|---|---|
| **{{COPILOT_NAME}}** | Keeps the list, sorts the feedback, refuses to widen the scope during acceptance |
| **{{CODING_AI}}** | Fixes the blocking items, and nothing else |
| **{{COACH}}** | Nothing, unless the switchover touches a paid plan |
| **You** | You use it, you note things, you train people, you decide the switchover day |

### 🚪 Exit gate, and it is the end of the project

Four things, together:

1. The parallel period is over and **no blocking item remains**.
2. The other users are trained on {{TARGET_DEVICE}}, with their own accounts.
3. **A backup has actually been restored**, and the date is noted.
4. The switchover is done; the old application stays reachable for {{FALLBACK_PERIOD}}, with its
   shutdown date noted.

### Known traps

- **Acceptance is the moment the urge to add comes back in force.** Anything that is not a blocking
  item goes into the "later" list, without discussion.
- Shutting the old one down on switchover day is the decision people regret. Keep the safety net.
- A user trained "by showing them the screen" is not trained. They are trained when they have done the
  journey themselves, on their own device.

---

## Step 11 — The first new feature: {{FIRST_NEW_FEATURE}}

*It is **named in advance**, from day one, and that is the whole point: naming it heads off "could we
just add this?" during the project. Deliberately thin on detail here, because it gets framed when the
time comes, against the real state of things. What matters is the barrier: this step does not open
before step 10 is closed.*

🔴 **This step does not open before step 10 is closed.** That is the rule protecting the whole project.
If an urgent want turns up meanwhile, it goes into the "later" list, which is precisely what that list
is for.

### To be framed with {{COPILOT_NAME}} when the step opens

*Put the questions that will have to be settled here, not the answers. A well-put question today beats
an invented answer that will be wrong when the time comes to build.*

- **The trigger**: who or what starts the feature, and how often.
- **The exact content** of what is produced.
- **The proof**: how do you know it actually happened? A silent mechanism that stops is the worst case.
- **The check**: how often we verify that the result is usable.

### 🚪 Exit gate

You see the expected result **yourself**, with nobody in between, and you can say when it was produced.

### And then?

The "later" list built up since step 2 becomes the new backlog. We go through it with
{{COPILOT_NAME}}, order it by value, and open the next batch: **one**, as always.

And we go back through the same path as step 3: **{{COPILOT_NAME}} gathers the requirement**. A line in
the "later" list is not a story, it is an intention, and it has to be picked up and written before it
enters the backlog, in `{{SPEC_DIR}}`, which is authoritative.

---

## Progress checklist

*One line per exit gate, never one more. The checklist is not a summary of the document, it is its
dashboard. Grouped into blocks matching the diagram's columns, so progress can be placed at a glance.
Each line is phrased in the first person, in the past, as an observed fact.*

### Preparation

- [ ] **1.** {{COPILOT_NAME}} answers respecting the step format; the {{REPO}} repository is visible in
      my account
- [ ] **2.** Framing note approved: like-for-like scope, hosting cost seen ({{HOSTING_COST}}, on
      {{COACH}}'s account, nothing new charged to me), "later" list open
- [ ] **3.** Backlog visible in the repository, read through and approved by me
- [ ] **3a.** I know where the specification (`{{SPEC_DIR}}`), the progress ({{TRACKING_BOARD}}) and
      the decisions ({{WIKI}}) live, and which of the three is authoritative
- [ ] **3b.** The repository really is **private**, and I know nothing goes public without {{COACH}}
- [ ] **4.** Request sent to {{COACH}}, invitation accepted, **the application appears in my
      {{HOSTING}} dashboard**
- [ ] **4a.** The application's exact name is noted somewhere other than in an email
- [ ] **4b.** {{CODING_AI}} confirms it can start the application on its side

### The foundation

- [ ] **5.** Empty home page live, checked from {{TARGET_DEVICE}}, with no wake-up delay
- [ ] **5a.** The `README.md` carries the live address in its first lines
- [ ] **6.** Structure document read and understood by me; the traps ticked one by one
- [ ] **7.** Sign-in working; {{RESTRICTED_ROLE}} is **refused** on an {{ADMIN_ROLE}} screen (not
      merely denied the link); a deactivated account loses access
- [ ] **7a.** {{SENSITIVE_DATA}} appears nowhere for {{RESTRICTED_ROLE}}
- [ ] **7b.** Security review passed on sign-in and permissions

### The value

*One line per module in {{MODULE_LIST}}, in order. The {{PIVOT_MODULE}} module carries the detailed
validation journey.*

- [ ] **8a.** Module 1 approved on {{TARGET_DEVICE}}
- [ ] **8b.** Module 2 approved on {{TARGET_DEVICE}}
- [ ] **8c.** Module **{{PIVOT_MODULE}}** approved: full journey, side effects checked
- [ ] **8d.** Module 4 approved on {{TARGET_DEVICE}}
- [ ] **8e.** Module 5 approved on {{TARGET_DEVICE}}
- [ ] **8f.** Module 6 approved on {{TARGET_DEVICE}}

### Migration and switchover

- [ ] **9.** Totals identical between the old and the new application
- [ ] **9a.** Five records spot-checked at random, including the known awkward cases
- [ ] **10.** Parallel acceptance finished, no blocking item left
- [ ] **10a.** Other users trained on {{TARGET_DEVICE}}, with their own accounts
- [ ] **10b.** A backup actually restored, at least once, date noted
- [ ] **10c.** Switchover done; the old application stays reachable for {{FALLBACK_PERIOD}}, shutdown
      date noted
- [ ] 🎉 **The project is finished**

### After

- [ ] **11.** {{FIRST_NEW_FEATURE}} working, result seen by me

---

*{{VERSION}} — {{DATE}}*
