# Template — Context (deliverable 4)

> **This template becomes `02-context.md` in `{{PACK_DIR}}`.**
> Its reader is **the AI, before any design decision**. It consolidates what is **already settled**, so
> that it stops being asked of {{RECIPIENT}} again.
>
> 🔴 **It does not copy the repository's sources**, it consolidates them, and it says **at the top which
> one wins** in a contradiction. Something that already lives in {{DOMAIN_DOCS_DIR}} is cited rather
> than duplicated: two texts saying the same thing always end up contradicting each other.
>
> 🔴 **No invented justification.** A missing reason becomes a named `⚠️ TO BE DECIDED` (who has to
> decide, and what), never a plausible hypothesis slipped in as a statement of fact.
>
> 🔴 **No secrets in the clear**: no password, no token, no key. Write **where** a credential is kept,
> never its value. This file is versioned and it will end up in an AI's knowledge space.
>
> *The italic lines under each heading are the filling-in instructions. They are removed from the
> produced deliverable, as is the table below.*

## This template's placeholders

🔴 **This section is removed from the produced deliverable.**

| Placeholder | What it stands for | Example |
|---|---|---|
| `{{PROJECT}}` | the project's or application's name | `Workshop Invoicing` |
| `{{PROJECT_PURPOSE}}` | what the application does, in one line | `issue quotes and invoices, and track stock` |
| `{{RECIPIENT}}` | first name of the person receiving the handover, who will steer | `Camille` |
| `{{COACH}}` | first name of the person handing over | `Alex` |
| `{{RECIPIENT_TRADE}}` | their actual work, in one line: what they are expert at | `runs an eight-person joinery workshop` |
| `{{RECIPIENT_LEVEL}}` | their real level, tool by tool, never "beginner" as a block | `complete beginner with AI and with Mac; comfortable in a spreadsheet` |
| `{{ORGANISATION}}` | the recipient's company or organisation | `the workshop` |
| `{{REPO}}` | the repository's short path | `my-org/workshop-invoicing` |
| `{{PACK_DIR}}` | the repository directory holding this pack | `docs/handover/` |
| `{{DOMAIN_DOCS_DIR}}` | the directory or directories already holding the domain documentation, **the authoritative sources** | `docs/product/` and `docs/specs/` |
| `{{CURRENT_APP_URL}}` | where the existing application runs | `https://workshop-invoicing.example.net` |
| `{{CURRENT_STACK}}` | the existing technical foundation | `the current live application` |
| `{{STACK}}` | the target technical foundation | `Django` |
| `{{HOSTING}}` | where the new application will go live | `Fly.io` |
| `{{CODING_AI}}` | the tool that writes and runs the code | `Codex` |
| `{{COPILOT_NAME}}` | the name given to the steering AI | `Workshop Copilot` |
| `{{VERSION}}` | the document's version | `v01` |
| `{{DATE}}` | the date it was last changed | `25/08/2026` |

---
---

# {{PROJECT}} — business and project context

This document is {{PROJECT}}'s **reference memory**, the thing that lets you {{PROJECT_PURPOSE}}. It is
read **before any design or coding decision**, whether the existing system is being evolved or rebuilt.

**What is settled here does not get asked of {{RECIPIENT}} again.** Every point in this document
already cost a discussion, a test or a bug. Reopening it with no new reason means paying for it twice.

🔴 **Which one wins.** The repository's sources, {{DOMAIN_DOCS_DIR}}, stay the reference for detail.
This document is their **consolidated reading**: where the two contradict each other, **the repository
source wins**, and this document is the one that gets corrected. Anything that appears neither here nor
there is not decided: ask about it, do not invent it.

*Instruction: keep this preamble as it is, adapting only the names. The three things it has to say are:
this is the memory; what is settled is not re-asked; who wins in a contradiction. A context with no
arbitration rule produces two truths at the first divergence.*

---

## 1. Who {{RECIPIENT}} is, the work, the working conditions

*Instruction: {{RECIPIENT_TRADE}}, {{RECIPIENT_LEVEL}}, {{ORGANISATION}}'s user profiles and what each
of them does in a day. 🔴 **Geography and hardware are not local colour**: each element translates into
a **constraint verifiable in the code**. A constraint not written here will be forgotten at
implementation time, and rediscovered by the user.*

### The profiles that use the application

*Instruction: one profile per row. Which device they work on, where, and what they do. This is what
will later justify the screen decisions, rather than an aesthetic preference.*

| Profile | What they work on, and where | What they do | What they never see or do |
|---|---|---|---|
| | | | |

### From observation to constraint

*Instruction: the right-hand column is the only one that matters to the AI, and it has to be
**verifiable**, meaning you can say yes or no by looking at the screen or the code. "Network sometimes
unstable" is not a constraint; "any long entry keeps a local draft and is resent when the network
returns" is one.*

| Observation | The verifiable constraint that follows |
|---|---|
| Network | |
| Devices and screen size | |
| Language and date format | |
| Currency and rounding | |
| Reference time zone for every period calculation | |
| Technical support available on site | |
| Applicable legal or tax framework | |

⚠️ The **reference time zone** is fixed here, once, explicitly, including when it does not match the
users' local time. Without that line, every monthly calculation drifts at random, and the figures stop
reconciling from one screen to the next.

## 2. The current state: what exists and runs

*Instruction: what today's application covers, what it does not, and how to reach it. A written
limitation does not get rediscovered; an unspoken one gets rediscovered in production, at the worst
moment.*

### What it does

*Instruction: the list of functional areas covered, one per line, in the language of the trade. No file
names and no technical components: this list is for knowing what already exists, not how it is built.*

-

### Known limitations, and why they are there

*Instruction: each limitation with **its reason** and **what it concretely prevents**. A limitation
whose reason is not written down gets "fixed" by the first AI that comes along, and the original
problem comes back.*

| Limitation | Why it exists | What it prevents |
|---|---|---|

### What is explicitly out of scope

*Instruction: what was deliberately set aside, and stays that way until {{RECIPIENT}} decides
otherwise. Without this list, every discarded feature gets proposed again in every conversation.*

-

### Access

*Instruction: where it runs, where the code lives, and **where** the credentials are. 🔴 Never the value
of a password, a key or a token in this file.*

- **Live application**: {{CURRENT_APP_URL}}
- **Code repository**: `{{REPO}}`, private
- **Test credentials**: *(say where they are kept, never what they are)*

## 3. Data structure, and the traps already paid for

*Instruction: the business entities, their structuring fields, their relations, and the structural
decisions already taken. Then, separately, the traps. This is **the section that stops an AI painfully
rediscovering a bug that was already fixed once**, and it is the first one people forget to write.*

### The structural decisions already taken

*Instruction: numbered, one per line, phrased as a decision rather than an observation. Each one answers
in advance a question that would otherwise come back at every screen design.*

1.

### The entities

*Instruction: one entry per entity: the fields carrying a rule, the calculated ones, and the ones
reserved for later. Do not copy the full schema if it already lives in {{DOMAIN_DOCS_DIR}}: point at it,
and keep here only what carries a decision.*

**`<entity>`** — structuring fields, calculated fields, constraints.

### What is reserved for later, and **must not be anticipated**

*Instruction: the extensions planned but not built. Naming them stops them being improvised
differently; saying they are not to be created stops them being built too early.*

-

### 🔴 Traps never to reintroduce

*Instruction: one per bug already met and fixed. **Three mandatory columns**: what happened; the rule
that prevents it; how you check the rule holds. A trap with no verifiable rule is an anecdote, and an
anecdote protects nothing. This is the part of the document {{CODING_AI}} has to read before writing a
single line of structure.*

| # | What happened | The rule that prevents it | How you check |
|---|---|---|---|
| 1 | | | |

⚠️ These traps are **independent of the technical foundation**. Changing language or database does not
make them go away: it makes them reappear in another form if nobody has rewritten them as rules.

## 4. Business rules and permissions by role

*Instruction: the invariant business rules, then the permissions matrix. The matrix is **the source of
truth for permissions**: whatever is not in it is not allowed.*

### Invariant rules

*Instruction: one rule per line, in the present tense, with no conditionals. A rule phrased as "it would
be good if" is not a rule, it is a wish, and the AI will arbitrate it in your place.*

-

### Permissions matrix by role

*Instruction: one section per module, one action per row, one column per role. Bold the cells that are
counter-intuitive: those are the ones an AI will spontaneously "correct" if nothing signals they are
deliberate.*

| Module | Action | *(role A)* | *(role B)* |
|---|---|:--:|:--:|
| | | | |

**General principle**: *(summarise in two sentences what the table says, so that a contradiction jumps
out. The summary and the table proofread each other.)*

### Edge cases already settled

*Instruction: the questions already asked and already answered: duplicates, deletions, sessions, expired
dates, empty entries, concurrent access. 🔴 **Do not ask {{RECIPIENT}} again.** That is exactly what
this document exists to prevent.*

-

## 5. The measures that matter

*Instruction: a dictionary, not a wish list. Each measure has an **unambiguous formula**, a **scope**
and a **visibility**. Fix the ones that are not built yet too: that is what stops them being redefined
at delivery time, when nobody remembers the intent any more.*

| Measure | Formula and scope | Visible to | Already delivered? |
|---|---|---|:--:|

**Authoritative notes**: *(the no-double-counting rules, what a cancellation removes, what is hidden
from which role. Two lines here beat a debate later.)*

## 6. The foundation chosen, and why

*Instruction: what has been chosen, and **the reason**. 🔴 If the reason for rebuilding something that
works is not documented, **do not invent it**: raise the `⚠️ TO BE DECIDED` below and name who has to
answer. A rebuild decision with no written justification gets re-argued at every difficulty, and a
project that gets re-argued is a project that stops.*

| | Today | Target |
|---|---|---|
| Technical foundation | {{CURRENT_STACK}} | {{STACK}} |
| Going live | | {{HOSTING}} |

**Why {{STACK}} rather than evolving {{CURRENT_STACK}}**:

⚠️ **TO BE DECIDED — the reason for the rebuild.** *(This heading is **mandatory** until the reason is
written down in black and white. Name who has to decide, usually {{COACH}}, and what is expected of
them. While it is open: presume no technical fault in the existing system, and offer {{RECIPIENT}} no
after-the-fact justification. Once the answer arrives, replace this heading with the reason, dated.)*

*Instruction: if the reason is already known, delete the `⚠️ TO BE DECIDED` block above and write the
reason in its place. Never keep both: a document carrying a justification and a warning saying it is
missing is no longer readable.*

## 7. 🔴 What must NOT change, and what is open

*Instruction: **two separate, explicit lists**. This is the most useful section of the document and the
one people forget. Without it, an AI treats everything as negotiable and redoes choices that were
already paid for. If something appears in neither list, it is not settled: ask.*

### Must not change

*Instruction: the product's invariants, independent of the technical foundation. For each, say **where**
it is defined in detail rather than copying it here.*

- **The data structure** from section 3: entities, relations, calculated fields, identifier rules.
- **The business rules** from section 4, and the **permissions matrix** exactly as it is.
- **The traps** from section 3. They are bugs already lived through and fixed once. They get
  reimplemented, not re-argued.
- **The measure definitions** from section 5, including the ones not yet built.
- **The discarded scope** from section 2: what is out of scope stays out, absent an explicit decision
  by {{RECIPIENT}}.
- **The constraints** from section 1: language, currency, devices, reference time zone.
- **The existing data**: it gets migrated, not recreated and not lost.
  *(Name here the real volumes and the anomalies already spotted in that data: a migration that
  discovers the anomalies along the way stops halfway.)*

### Open

*Instruction: what the AI may propose on without asking again. An empty list is an alarm signal:
nothing is ever entirely fixed, and a document that opens nothing produces a stalled project.*

- **The technical foundation** itself and all the implementation machinery: how the code is split,
  libraries, conventions, tests.
- **The final hosting choice**, to be settled with its own pricing in hand.
- **The visual styling**, as long as the constraints in section 1 hold.
- **The delivery order** and the lower-priority features: {{RECIPIENT}} can resequence or drop them
  freely.

## 8. What the old foundation was giving away for free

*Instruction: 🔴 **the section that appears in no requirements document, and the number one regression
risk of a rebuild.** Changing foundation makes guarantees disappear that nobody had asked for, because
the old tool provided them without anyone thinking about it. Each one gets reimplemented **by name**,
with an owner and a way of checking it is actually there.*

| What was provided without being asked for | What provided it | What has to be rebuilt in {{STACK}} | How you check it is there |
|---|---|---|---|
| Data separation between roles | | | |
| Sensitive columns blocked at the storage level | | | |
| Consistency constraints enforced by the database | | | |
| Backups, and a restore that has been tested | | | |
| Encrypted traffic and session handling | | | |
| Access and error logging | | | |
| Reversible structural migrations | | | |

⚠️ **A row of this table left empty is a security or data hole**, not a finishing detail.
{{COPILOT_NAME}} checks it **before** going live, never after: afterwards, you no longer discover the
hole, you discover its consequences.

*Instruction: add the rows specific to this project and delete the ones that do not apply. A row is
removed because it is genuinely irrelevant, never because nobody knows what to put in it. In that case
it becomes a `⚠️ TO BE DECIDED`.*

---

*{{VERSION}} — {{DATE}}*
