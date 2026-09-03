# Template — Stack and technical decisions (deliverable 5)

> **This template becomes `03-stack-and-technical-decisions.md` in `{{PACK_DIR}}`.**
> Its reader is **the AI that codes**, and it reads it **before writing a single line**. The recipient
> will probably never open it, so the document is allowed to be dense and required to be precise.
>
> 🔴 **Prescriptive, never descriptive.** You do not write here what the system does: you write what
> the AI is allowed to do, what it is not allowed to do, and how it checks that for itself. A sentence
> that does not translate into "I can see that this holds" has no place in this document.
>
> 🔴 **Every known trap of the old system is translated here into a verifiable rule.** A trap that is
> narrated instead of translated into a rule will be reintroduced. That is mechanical, not
> hypothetical.
>
> 🔴 **Do not rewrite the project method.** Ready and Done, the specification that generates the
> backlog, milestones and board live in `{{METHOD_REPO}}`. This **points** at them, rather than
> copying them.

## This template's placeholders

🔴 **This section is removed from the produced deliverable.**

| Placeholder | What it stands for | Example |
|---|---|---|
| `{{PROJECT}}` | the project's or application's name | `Workshop Invoicing` |
| `{{RECIPIENT}}` | first name of the person receiving the handover, who will steer | `Camille` |
| `{{COACH}}` | first name of the person handing over | `Alex` |
| `{{COPILOT_NAME}}` | the name given to the steering AI | `Workshop Copilot` |
| `{{CODING_AI}}` | the tool that writes and runs the code | `Codex` |
| `{{REPO}}` | the repository's short path | `my-org/workshop-invoicing` |
| `{{REPO_HOST}}` | where the repository is hosted | `GitHub` |
| `{{PACK_DIR}}` | the repository directory holding this handover pack | `docs/handover/` |
| `{{DOMAIN_DOCS_DIR}}` | the directory or directories already holding the domain documentation | `docs/product/` and `docs/specs/` |
| `{{SPEC_DIR}}` | the directory where the specification and stories land, **the authoritative one** | `docs/specs/` |
| `{{CURRENT_SCHEMA_DOC}}` | the document describing the current data structure | `docs/specs/data-model.md` |
| `{{TRACKING_BOARD}}` | the tool carrying progress, one card per story | `the repository's Projects board` |
| `{{WIKI}}` | where a human goes to read decisions and procedures, outside the code | `the repository wiki` |
| `{{METHOD_REPO}}` | the method template repository being pointed at | `my-org/kickoff` |
| `{{CODE_STANDARD}}` | the mandatory idiom reference for the chosen language | `the house skill of framework idioms` |
| `{{STACK}}` | the target stack, as a short phrase | `Laravel + MySQL` |
| `{{CURRENT_STACK}}` | what runs the application today | `a no-code generator and its hosted database` |
| `{{HOSTING}}` | where the application goes live, on the coach's account | `Fly.io` |
| `{{HOSTING_COST}}` | what the hosting costs per month, once live | `~$8/month` |
| `{{LOCAL_CURRENCY}}` | the currency the recipient thinks in day to day | `euros` |
| `{{APP_LANGUAGE}}` | the interface language, without exception | `French` |
| `{{TIMEZONE}}` | the reference time zone for splitting periods | `Europe/Paris` |
| `{{USER_CONTEXT}}` | where and in what physical conditions the users work | `in the field, on the move, on an unstable mobile network` |
| `{{TARGET_DEVICE}}` | the device the application is actually used on | `an entry-level phone` |
| `{{AUTH_TOOL}}` | the component handling credentials, sessions and forgotten passwords | `the framework's standard authentication component` |
| `{{AUTHZ_TOOL}}` | the component deciding who is allowed to do what | `a per-resource authorisation rule layer` |
| `{{ADMIN_ROLE}}` | the role that sees and can do everything | `administrator` |
| `{{RESTRICTED_ROLE}}` | the limited role, the one the regression check targets | `field worker` |
| `{{SENSITIVE_DATA}}` | what `{{RESTRICTED_ROLE}}` must see **nowhere** | `pay data` |
| `{{PIVOT_ENTITY}}` | the model's central entity, the one carrying the core rules | `job` |
| `{{DATA_VOLUME}}` | what there is to migrate, in real volume | `around 200 files, 40 workers and three years of history` |
| `{{VERSION}}` | the document's version | `v01` |
| `{{DATE}}` | the date it was last changed | `25/08/2026` |

---
---

# {{PROJECT}} — stack and technical decisions

## What this document is for

*The preamble answers three questions and not one more: what this document is for, who reads it, and
**what is authoritative elsewhere**. The third is the one people forget, and it is the most useful:
without it, the coding AI re-decides the business rules as it goes, because it does not know where to
read them.*

This is **{{PROJECT}}'s reference technical brief**. It is written to be read by {{CODING_AI}} **before
a single line of code is written**, and read again whenever an architecture question comes up. It does
not describe the business: it **translates into technical decisions** invariants that were already
validated elsewhere.

**What is authoritative elsewhere, and must not be re-decided here:**

| Subject | Authoritative document |
|---|---|
| Business, data structure, business rules, permissions by role, definitions of the figures | `{{PACK_DIR}}02-context.md` |
| Working method and roles, who approves what | `{{PACK_DIR}}00-method-and-roles.md` |
| Steps, exit gates, progress checklist | `{{PACK_DIR}}01-phasing-and-checklist.md` |
| Product documentation and business rules already written | `{{DOMAIN_DOCS_DIR}}` |
| The current system's actual data structure | `{{CURRENT_SCHEMA_DOC}}` |
| Mandatory code idioms | `{{CODE_STANDARD}}`, restated in §3 below |
| Ready and Done, specification to backlog, milestones | `{{METHOD_REPO}}` |

🔴 **The reading rule in a contradiction**: the context document wins on **business**, this document
wins on **technical**. If the contradiction covers both at once, it is a question for {{RECIPIENT}},
not a decision for {{CODING_AI}}.

🔴 **Scope: like for like.** The target does what the existing system does, no more and no less. Any
idea for a new feature that comes up along the way goes into the backlog; it does not get coded (§11).

---

## 1. Target stack

*One table, four columns: layer, choice, target version, **why**. The fourth column is not decorative:
it has to let the AI **defend the choice**, not merely apply it. An AI that knows why a component was
picked does not propose replacing it at the first difficulty, and can say when the reason no longer
holds.*

*A version is **pinned**: the same value locally and live, written into a file in the repository. A
version of "the latest" is a version that will change without warning, on a Tuesday morning.*

| Layer | Choice | Target version | Why |
|---|---|---|---|
| Language | | | *the reason, in one sentence* |
| Framework | | | |
| Database | | | *if it is the same engine as today, say so: what transposes as is does not get rewritten* |
| Starting skeleton | | | |
| Assets / CSS | | | |
| JavaScript | | | *say what this choice replaces, and what it lightens* |
| Authentication | {{AUTH_TOOL}} | | |
| Authorisation | {{AUTHZ_TOOL}} | | *the most sensitive point, see §6* |
| Forms | | | |
| Translations and formats | | | *interface entirely in {{APP_LANGUAGE}}* |
| Printable documents | | | *prefer what needs no system binary: every system dependency is a deployment risk* |
| Environment variables | | | |
| Tests | | | |
| Static analysis and security | | | |
| Hosting | {{HOSTING}} | | *on {{COACH}}'s account, see §9* |

⚠️ **Check the starting skeleton's compatibility before the first commit.** A project template that has
not kept up with the framework's latest version produces an application that will not start. If it
breaks: **do not patch around it.** Pin an older version, regenerate, and write the chosen version into
the `README.md`.

---

## 2. 🔴 What disappears from the old foundation, and what replaces it

*🔴 **The most important section of the document.** {{CURRENT_STACK}} was providing, for free, things
nobody ever wrote into a requirements document: security carried by the infrastructure, constraints
enforced by the database, backups, consistency guarantees. They **disappear with it**, with no error,
no warning, and no way of noticing before the incident.*

*It is the number one regression risk of a change of foundation. Filling in this table is not a
formality: it is the most profitable piece of analysis in the whole project. A row marked "not
applicable" has to say **why** it is not applicable, rather than merely asserting it.*

| What {{CURRENT_STACK}} provided | What replaces it in {{STACK}} | Where it is handled |
|---|---|---|
| *authentication and sessions* | {{AUTH_TOOL}} | §6 |
| *per-user row filtering, enforced by the database* | {{AUTHZ_TOOL}}, **and nothing else** | §6 |
| *masking a sensitive column, enforced by the database* | *a query that does not select the column* | §6 |
| *views or procedures carrying a security rule* | | §6 |
| *privileged server-side functions* | | §5 |
| *the public key used by the browser* | *not applicable: no more direct database access from the browser* | §6 |
| *constraints and guardrails set in the database* | *to be re-laid by name, one by one* | §4, §5 |
| *automatic backups* | | §9 |
| *calculation and aggregate views* | | §5 |
| *rendering the interface* | | §7 |

🔴 **A consequence to absorb before writing the first screen**: where the old foundation caught an
oversight, there is now **nothing behind**. A forgotten check is no longer a small flaw, it is full
access. Write that sentence into the deliverable, naming the component concerned: it is what justifies
every rule in §6.

---

## 3. The non-negotiable rules

*A numbered list of **verifiable prohibitions**: "NEVER X", "ALWAYS Y". The phrasing matters more than
the content, because the AI has to be able to **self-check against this list before every delivery**,
answering yes or no to each line. A rule beginning with "prefer", "as far as possible" or "avoid" is
not verifiable: rephrase it or remove it.*

*The substance of the list comes from `{{CODE_STANDARD}}`, the idiom of the chosen language, which is
what makes the code readable by someone else. Add the rules below, which hold whatever the stack.*

1. **NEVER a hard-coded secret.** The code reads an environment variable; the variable's **name** is
   versioned in an example file, in the same commit; the **value** lives in the unversioned local
   configuration and in {{HOSTING}}'s. No "just for this test" exception.
2. **NEVER a network call to a third-party domain from a served page**: fonts, icons, scripts,
   analytics. Every front-end dependency is downloaded and served by the application (§7).
3. **NEVER refactor what works** without an explicit request: no renaming in passing, no extracting a
   method to factor out two pieces that look alike. The same code twice is acceptable; on the third,
   you **flag** it rather than doing it.
4. **NEVER a construct outside the standard's programme**: metaprogramming, home-made indirection,
   dense one-liners. When a less common construct is the right tool, use it **and add a one-line
   comment saying what it produces**.
5. **NEVER create anything on {{REPO_HOST}} on its own initiative** beyond branches and change
   proposals: no board, no {{WIKI}} page, no change to the repository's visibility (§8).
6. **NEVER provision a paid resource** at {{HOSTING}} or anywhere else on its own initiative (§9).
7. **ALWAYS write the test from the acceptance criterion**, watch it fail, then write the minimum that
   makes it pass. The test's name is a deliverable: it describes the behaviour refused or expected,
   never "it works".
8. **ALWAYS break the work into numbered comments before writing a function**, and **leave the
   comments in the delivered code**. If a step does not fit in one comment line, it deserves its own
   function.
9. **ALWAYS build in silos**: one complete page (route, processing, screen) checked in the browser
   before starting the next. Never all the routes, then all the processing, then all the screens.
10. **ALWAYS one story, one branch**, named after it.
11. **ALWAYS database guardrails in addition to application checks.** A guardrail that lives only in
    the code falls at the first data import (§10).
12. **ALWAYS read the acceptance criterion in `{{SPEC_DIR}}`**, never in a {{TRACKING_BOARD}} card nor
    in a {{WIKI}} page (§8).

*Add the rules specific to the chosen stack here, in the same form. Aim for a list that can be reread
in two minutes: beyond about twenty lines, a list of rules stops being reread.*

---

## 4. Foundation decisions, to be settled before the first line

*These are the decisions that are expensive to change once data exists. They are settled **before** the
first data structure, not when the question comes up. For each: the choice, the reason, and what breaks
if it changes later.*

| Decision | What has to be settled | Why now |
|---|---|---|
| **Identifiers** | which kind of key for each record, and whether to **keep the current system's identifiers** | Keeping them makes the migration nearly free: the links between tables already point at the right values, with nothing to remap. Changing them is paid once, at import, and forever |
| **Human-readable references** | the references shown on screen and printed | 🔴 **They are never used as a join key.** A readable reference is searched for and printed; it does not link two tables. A relation pointing at a readable reference is a bug |
| **Format of the versioned data structure** | the format the schema is stored in, in the repository | Many tools' default format cannot represent fine-grained constraints, computed columns or unusual types. If the database has any, the full format is required, otherwise the guardrails vanish silently at the first reload |
| **Time zone and dates** | {{TIMEZONE}} as the reference zone, and the display format in {{APP_LANGUAGE}} | A monthly figure calculated in one zone and read in another gives two different totals for the same month. That is the kind of gap that takes weeks to explain |
| **Amounts** | the storage unit: **integers in the smallest unit**, never a floating-point number | An amount in floating point produces totals that are wrong by a penny, in exactly the place where nobody accepts it. Display goes through a dedicated function, never in the screen |
| **Fractions and percentages** | for each rate: **fraction or percentage**, and the constraint that guarantees it in the database | A rate stored sometimes as `0.1` and sometimes as `10` produces discounts off by a factor of a hundred. The database constraint is the only protection that survives an import |
| **Statuses** | the closed list of each entity's states, backed by a **database constraint** | A free-text status ends up holding values no screen knows how to display |
| **Numbering** | for each counter: the prefix, the length, and **whether it has to be gapless** | "Gapless" and "unique" are not the same requirement, and do not have the same implementation. Settle which counters are concerned |

*For each row, write **the decision taken** into the deliverable, not just the question. A foundation
decision left open will take itself, by default, at the first file written.*

---

## 5. Old to new mapping, entity by entity

*One section per entity, always the same anatomy. This is the heart of the document and its longest
part, and it is also what stops everything that was already paid for once being rediscovered by hand.*

*🔴 **The rule governing this section**: each known trap of the old system is translated here into a
**verifiable rule** in the new one. A narrated trap ("careful, that column is special") will be
reintroduced; a translated trap ("no writes to that column, the database computes it, and a test proves
it") will not.*

The anatomy to repeat for each entity:

| Heading | What goes in it |
|---|---|
| **Old name → new name** | and any renaming, with **the reason**. A renaming with no written reason gets re-argued |
| **Fields** | one by one, with the chosen type and whether it is required |
| **Relations** | what they point at, and the delete behaviour, **chosen from the business rule**: not everything cascades, and some relations must instead **refuse** the deletion |
| **Database constraints** | the guardrails the database refuses to let through |
| **Business rules** | what the code has to guarantee on top |
| **Attached traps → verifiable rule** | the trap in one line, the rule that prevents it, and **the test that proves it** |

### The existing system's traps, translated

*Number them: the exit gate of the "data structure" step consists of ticking them off one by one, and
an unnumbered list cannot be ticked. Each trap fits in three lines: the symptom, the rule, the test.*

*Families of traps that recur from one project to the next, worth checking even if nobody flagged
them:*

- **A join key pointing at a readable reference** instead of the real key.
- **A column computed by the database** that an import or a form would try to write to.
- **A rate stored in one unit and read in another.**
- **Numbering assigned too early**, leaving a gap when the operation fails.
- **A quantity that can go below zero** when two operations cross.
- **A price frozen at entry time** that would start following the current tariff again.
- **A missing value treated as a zero** instead of staying empty.

### {{PIVOT_ENTITY}}, the central entity

*Handle it first and in detail: it carries the core of the rules, and it is the one the AI will get
wrong if the document is vague. Describe its life cycle state by state, what becomes immutable and
when, and **what moves elsewhere** when it changes state. An operation touching several tables happens
in a single transaction, or it does not happen.*

---

## 6. Authorisation and permissions

*A dedicated section, never a paragraph slipped in elsewhere. This is where what {{CURRENT_STACK}}
provided for free gets reimplemented, and it is the section whose absence causes the most silent
damage.*

### 6.1 Why this is the number one regression risk

*Write this reasoning out in full in the deliverable, with the real component names. It is what
justifies every action authorising, without exception. Without it, the discipline erodes by the third
screen.*

Where {{CURRENT_STACK}} carried part of the security **outside the application**, {{STACK}} has only
**one barrier on the server side**: {{AUTHZ_TOOL}}. There is nothing behind it any more.

🔴 **A forgotten authorisation check is not a small flaw, it is full access.**

### 6.2 The rules

1. **Deny by default.** Anything not explicitly allowed is refused. One authorisation rule per
   resource, never a check scattered across the screens.
2. **Every action authorises, without exception**, including the innocuous-looking pages.
3. **A net that makes an omission loud.** The foundation must **fail** when an action has not
   authorised, rather than letting it through. An omission has to produce an error, not a leak.
4. **The restriction applies to the data, not to the display.** Forbidden data is not hidden on
   screen: it **is not read**. The filtering happens in the query.
5. **The fields accepted for writing depend on the role.** A restricted role sending a field it may
   not change must see that field ignored, not applied.
6. **A deactivated account loses access immediately**, current session included.
7. **No enumeration.** Sign-in and forgotten-password error messages never say whether an account
   exists.

### 6.3 Regression checklist against the old system

*🔴 **This checklist is the section's deliverable.** One line per guarantee the old foundation
provided, and its named equivalent in the new one. To be ticked **before the first real deployment**,
and revisited at every security review.*

| # | What the old foundation provided | Equivalent in {{STACK}} | Verified by |
|---|---|---|---|
| 1 | *per-user row filtering, held outside the application* | *an authorisation in every action* | *the net that makes an omission loud, plus one test per screen* |
| 2 | *read access restricted by role* | *a filtered query in every list* | |
| 3 | *masking a sensitive column* | *a query that does not select the column* | *a test that searches for the value in the full response* |
| 4 | *views or procedures carrying a security rule* | | |
| 5 | *role checks in server-side functions* | | |
| 6 | *no privileged key on the browser side* | | |
| 7 | *no API key in the served page* | *a search through the screen templates* | |
| 8 | *session invalidated for a deactivated account* | | |
| 9 | *no address enumeration on forgotten password* | | |
| 10 | *consistency constraint enforced in the database* | | *a concurrency test* |
| 11 | *gapless numbering* | | *a test: a failed operation consumes no number* |

🔴 **Line 1 is the only one that truly matters; the others are its consequences.** An action that does
not authorise makes all the others pointless.

### 6.4 The test that proves it holds

*Write it out explicitly, because it is counter-intuitive: the test is not about checking that a link
does not appear.*

A {{RESTRICTED_ROLE}} account requests directly the address of a screen reserved for {{ADMIN_ROLE}}: it
must get a **refusal**. And {{SENSITIVE_DATA}} must appear **nowhere** for them: not on screen, not in
an export, not in a search, not in a total that would let it be deduced. The test searches for the
value in the **full response**, not in what is displayed.

---

## 7. Field constraints

*🔴 **This is not local colour.** The users' physical and geographical context translates into
**verifiable consequences on the code and the interface**. A field constraint written as an anecdote
("they sometimes have signal") changes nothing in the code; written as a rule ("no request to a
third-party domain from a served page") it can be checked and it holds.*

*If there really is no particular constraint, write that down, but check first: an absence of
constraints is almost always a question nobody asked.*

The users work {{USER_CONTEXT}}, on {{TARGET_DEVICE}}. This is not a secondary usage context, it is the
main one. The decisions below follow from it and are not negotiable "to go faster".

| Field constraint | Consequence on the code | How it is checked |
|---|---|---|
| **Unstable or slow network** | 🔴 no request to a third-party domain from a served page: fonts, icons, scripts and analytics are downloaded and served by the application | a search through the served files finds no external address |
| **Modest devices** | light pages, server-side rendering, no heavy single-page application; a written weight budget per page | measuring the weight of the heaviest page |
| **Cut off mid-entry** | 🔴 a long form **survives a disconnection**: the entry is kept locally and restored on return. A record lost after ten minutes of typing makes people abandon the application for good | a real trial: cut the network mid-entry, come back |
| **Real mobile use** | designed for the narrow screen first; large enough touch targets, no hover as the only way in, no wide table without a fallback | each module is validated on {{TARGET_DEVICE}}, not on a computer |
| **Language, currency, formats** | interface entirely in {{APP_LANGUAGE}}; amounts in {{LOCAL_CURRENCY}} in the local format; dates in the local format; periods split on {{TIMEZONE}} | no interface string outside {{APP_LANGUAGE}}, technical error messages included |

⚠️ **Beware the tools' defaults.** Many front-end dependency tools point by default at an external
distribution service. That is the default, and it is exactly what is not wanted here: the local
download has to be requested explicitly, and **the resulting configuration file checked**.

---

## 8. Where the work lands

*Three places, three uses, **only one authoritative**. This section is not about organisation: it
determines **where the AI reads an acceptance criterion** before writing a test. Without it, it will
code on the strength of a board card nobody updated.*

| Place | What it carries | Authoritative |
|---|---|---|
| **The repository's `{{SPEC_DIR}}`** | the specification and the stories, as versioned files | 🔴 **yes** |
| **{{TRACKING_BOARD}}** | progress: one card per story, **derived** from the files | no, it regenerates |
| **{{WIKI}}** | what a human reads outside the code: decisions and their reasons, procedures | for its own subject only |

Operational consequences for {{CODING_AI}}:

- **The source of an acceptance criterion is the file in `{{SPEC_DIR}}`**, never a card nor a {{WIKI}}
  page. If a card contradicts a file, the file wins and the card is regenerated.
- A story is produced by {{COPILOT_NAME}} and approved by {{RECIPIENT}}; {{CODING_AI}} **executes** it,
  it does not invent it. A story that cannot be demonstrated on screen is not a story.
- **Never a specification copied into {{WIKI}}.** A specification in two places is a specification one
  of whose copies is already wrong.
- 🔴 **The {{REPO}} repository is private by default.** No switch to public is decided without
  {{COACH}}, whatever reason is given: the repository holds business rules and real data.

🔴 **What {{CODING_AI}} may create**: branches and change proposals. **Nothing else** on {{REPO_HOST}}:
no board, no {{WIKI}} page, no visibility change, while that has not been explicitly settled.

⚠️ **TO BE DECIDED if it has not been already**: *who* actually creates the {{TRACKING_BOARD}} cards
and the {{WIKI}} pages. {{CODING_AI}} if it has the access, {{RECIPIENT}} through the web interface, or
{{COACH}}. Until that is decided, the rule above applies without exception.

---

## 9. Deployment

*Two things to write, and one prohibition. The two things: **whose account the application lives on**,
and **what access was granted once and for all**. The prohibition: provisioning anything paid.*

### 9.1 The access model

The application lives on {{COACH}}'s {{HOSTING}} account. **{{RECIPIENT}} opens no account and provides
no card**, so never ask them to, even when a screen appears to require it.

{{COACH}} **grants access once**, as a collaborator on {{HOSTING}} and on {{REPO}}, and {{RECIPIENT}}
is **autonomous from then on**: they deploy, read the logs, restart the application.

🔴 **Never invent a standing request ritual.** "Ask {{COACH}} before every deployment" puts back on the
critical path someone who is precisely no longer available day to day: the setup stops at the first
slow reply. Three things only go to them: the initial granting of access, anything touching billing or
a paid plan, and making the repository public.

### 9.2 🔴 No paid resource on its own initiative

**{{CODING_AI}} never provisions a paid resource**: an additional service, a higher tier, an extra
environment, a domain name. It **proposes**, prices it, and waits. A service added "because it would
make things simpler" is a line on an invoice nobody saw coming, on somebody else's account.

One live environment, absent an explicit decision. A test environment left running costs money every
month and produces nothing.

### 9.3 What has to be set up, in order

*Number the real sequence: creating the application, configuration, database, environment variables,
first deployment, automation. For each step, **what you should see** at the end, not just the command.*

### 9.4 Environment variables

*A `Variable | Required | Use` table, with the real values never versioned. Each variable's name is
added to the example file **in the same commit** as the code that reads it.*

### 9.5 Backups

*Write: what is backed up, how often, where it lives, and **how long it is kept**. Then the rule:
🔴 **a backup that has never been restored is not a backup.** A real restore has to be done at least
once before the switchover, and the date noted. Do not declare backups "in place" before that check.*

### 9.6 The cost, on {{COACH}}'s account, and stated anyway

*🔴 Someone else paying never excuses not stating a cost. What {{RECIPIENT}} needs to know is what
their application consumes, and it is also what makes it immediately visible when a figure doubles for
no reason.*

| Item | Monthly cost | Who pays |
|---|---|---|
| | | {{COACH}} |
| | | |
| **Total** | **{{HOSTING_COST}}** | **{{COACH}}, nothing charged to {{RECIPIENT}}** |

*Convert the total into {{LOCAL_CURRENCY}} and into an annual cost: it is the order of magnitude that
speaks, not the unit price. And state the caveats rather than leaving them out: billing in a foreign
currency fluctuates, and a small tier offers fewer guarantees than a large one. These prices are a
**dated order of magnitude, not a quote**, to be rechecked at creation time.*

---

## 10. Data migration

### 10.1 The rule that overrides all the others

🔴 **No real data is lost, nothing is recreated from scratch, and no value is invented.**
{{DATA_VOLUME}}: this is the history of a running business, not a test fixture. Data that cannot be
imported is **flagged**; it is not guessed and it is not deleted.

### 10.2 The strategy

*Describe it in three points: where the data comes from, where it lands meanwhile, and what imports it.
Two things not to forget:*

- *The directory receiving the export files is **excluded from version control**: it holds real data.
  Its **name**, however, is documented.*
- *An import is not a demo data set. What is wanted is a detailed report and the ability to **rerun
  without duplicating**. Those are two different requirements and they change the tool.*

### 10.3 What the import has to guarantee

| Requirement | What it means |
|---|---|
| **Replayable without duplicating** | each record is found by its original identifier. Rerunning creates nothing twice |
| **Identifiers preserved** | that is the whole point of the foundation decision in §4: the links between tables already point at the right values, with nothing to remap |
| **All or nothing** | the entire import goes through, or none of it does |
| **Order respected** | referenced entities before the ones that reference them |
| **Computed columns ignored** | never write a value the database computes, even when it appears in the source file |
| **Renamings applied** | the ones decided in §5, and only those |
| **Checks bypassed only where needed** | the history holds states today's rules refuse. Bypass **only** on historical rows, never in the application code, and log every case |
| **A written report** | rows read, created, skipped, **with the reason** |

### 10.4 After the import: the mandatory steps

1. **Initialise the counters** at the maximum already used, otherwise the next number overwrites an
   existing one. *Write a table: entity, prefix, length, value after import.*
2. **Recompute the derived values** from the imported data, then run the consistency check. The report
   must be empty. A discrepancy is a bug to understand, not to erase.
3. **Acceptance checks**, compared against the existing system before declaring the import successful:
   the totals, the counts per entity, and a handful of records opened at random and compared on
   screen.

### 10.5 Known anomalies, and their prescribed handling

*List them one by one, with their handling. The rule: an anomaly is **migrated as is** and corrected
afterwards from the application, by hand, with a trace. An anomaly "cleaned up" in passing is a
discrepancy in a total that nobody will be able to explain six months later.*

| Anomaly | Handling | To be decided |
|---|---|---|
| *unreadable data in a numeric field* | *import what is readable, isolate the rest in an anomalies file with its raw content* | *what that value represented, by {{RECIPIENT}}* |
| *an empty but numbered record* | *import as is, in whichever state fits. The number stays reserved and the numbering stays gapless* | *what those numbers represented* |
| *missing dates* | 🔴 *never invent a date nor derive it from another column. Leave it empty and list every case in the report* | *provide the real dates, or accept the state* |
| *a value absent where that is normal* | *expected behaviour, not an anomaly: the value stays empty and the display hides it without error* | — |

🔴 **None of these questions blocks the project.** The import happens, the anomalies are imported in
their documented state, and the correction happens later from the application. Do not wait for the
answers to move forward on the code.

---

## 11. What we do NOT do

*The list of temptations to refuse. Each one is a good idea, in another project or later.
🔴 **An idea that appears in this list goes into the backlog and does not get coded.** Write it down: an
unnamed temptation will be given in to, with the best intentions in the world.*

### 11.1 No new features

*Take the list from the context document, as it is. And add the rule people forget:*
🔴 **the slots "reserved for later" do not get created.** An empty table created in anticipation is a
table that gets migrated for years without ever being used.

### 11.2 No refactoring of what works

- No renaming of a table or a field, **except** those decided in §5, with their written reason.
- No translating the business vocabulary. The terms {{RECIPIENT}} uses stay as they are in the code:
  it is their vocabulary, and it is carried over identically from the existing system.
- No extra indirection: home-made layers, service objects, just-in-case abstractions.
- No "while we're at it" on the business rules. An edge case already settled in the context document
  does not get re-argued, even when it looks arguable.

### 11.3 No change of technical scope

| Temptation | Why not |
|---|---|
| *replacing a component from §1 with another, better-known one* | *it comes with the skeleton, and it is known to whoever will review* |
| *a just-in-case programming interface* | *nobody consumes it, and every entry point is one more authorisation surface* |
| *a full offline mode* | *the existing system is online only; the local form save (§7) is the answer chosen* |
| *an asynchronous job queue* | *no asynchronous processing is in scope: one more service, one more cost* |
| *a generic admin interface* | *account management is a set of simple screens with their own authorisation rules* |
| *a containerised development environment* | *nobody on the team will maintain it* |
| *an elaborate integration pipeline* | *green tests before the change proposal, plus the security analysis at review* |
| *running both versions in parallel* | *one application is authoritative. The switchover is a dated moment, not a transition* |

### 11.4 On method

- **No code before the routes and before the tests.**
- **No large batches.** One story, one branch, one change proposal. A batch that does not fit in one
  pass gets split.
- **No screen without an authorisation rule**, including the innocuous-looking pages.
- **No specification written anywhere but in `{{SPEC_DIR}}`** (§8).
- **No initiative on {{REPO_HOST}}** beyond branches and change proposals (§8).

---

## 12. Summary of what is still to be decided

*🔴 **Mark `⚠️ TO BE DECIDED` rather than inventing.** A justification invented because the real one
was missing is this document's most expensive defect: it looks like a decision, it gets cited like a
decision, and nobody knows any more that it is not one.*

*For each point: who decides, and **blocking or not**. The second column matters as much as the first:
a non-blocking point must never become a pretext for waiting. Say explicitly what can move forward
meanwhile.*

| # | Point | Who decides | Blocking? |
|---|---|---|---|
| 1 | | | *No: we develop meanwhile, and settle it before going live* |
| 2 | | | |
| 3 | | | |

### Settled since, do not reopen

*The block people always forget, and the one that saves the most time. A settled decision that is not
written here will be questioned again at the first difficulty, and an AI that re-argues a settled
decision wears a beginner out faster than any bug.*

- **Who holds the accounts and the card.** The application lives on {{COACH}}'s {{HOSTING}} account,
  and they add {{RECIPIENT}} as a collaborator; {{RECIPIENT}} opens no account and provides no card
  (§9.1).
- **The scope is like for like.** The target does what the existing system does, no more and no less
  (§11).
- **The repository is private by default** (§8).
- *Add every decision settled as the project goes, with the section that carries it.*

---

*{{VERSION}} — {{DATE}}*
