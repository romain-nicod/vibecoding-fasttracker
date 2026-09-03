# Template — Getting started (deliverable 1)

> **This template becomes the handover pack's `README.md`**, at the root of `{{PACK_DIR}}`.
> It is the first and sometimes the only file the recipient will read. They have to be able to go
> from nothing to "my AI has taken over" **alone, unaided, on a Friday evening**.
>
> 🔴 **Zero terminal commands.** Every action names the page to go to, the exact button label, and
> **what they should see at the end** to know it worked.

## This template's placeholders

🔴 **This section is removed from the produced deliverable.** It exists only for whoever fills it in.

| Placeholder | What it stands for | Example |
|---|---|---|
| `{{RECIPIENT}}` | first name of the person receiving the handover, who will steer | `Camille` |
| `{{COACH}}` | first name of the person handing over | `Alex` |
| `{{PROJECT}}` | the project's or application's name | `Workshop Invoicing` |
| `{{ORGANISATION}}` | the recipient's company or organisation | `the workshop` |
| `{{REPO}}` | the repository's short path, as it displays | `my-org/workshop-invoicing` |
| `{{REPO_URL}}` | the repository's full URL | `https://github.com/my-org/workshop-invoicing` |
| `{{REPO_HOST}}` | where the repository is hosted | `GitHub` |
| `{{CODING_AI}}` | the tool that writes and runs the code | `Codex` |
| `{{STEERING_AI}}` | the form the steering AI takes: configured assistant, project space, prompt | `a configured assistant` |
| `{{COPILOT_NAME}}` | the name given to that assistant, as it will appear in the sidebar | `Workshop Copilot` |
| `{{AI_PLAN}}` | the paid plan giving access to both AIs | `ChatGPT Pro` |
| `{{STEERING_AI_SETUP_URL}}` | the page where the steering AI is configured | `https://chatgpt.com/gpts/editor` |
| `{{DIAGRAM_TOOL}}` | the drawing tool for wireframes and diagrams | `Excalidraw` |
| `{{HOSTING}}` | where the application goes live, on the coach's account | `Fly.io` |
| `{{PACK_DIR}}` | the repository directory holding this pack | `docs/handover/` |
| `{{DOMAIN_DOCS_DIR}}` | the directory or directories already holding the domain documentation | `docs/product/` and `docs/specs/` |
| `{{METHOD_REPO}}` | the method template repository being pointed at | `my-org/kickoff` |
| `{{METHOD_REPO_URL}}` | its full URL | `https://github.com/my-org/kickoff` |
| `{{VERSION}}` | the document's version | `v01` |
| `{{DATE}}` | the date it was last changed | `25/08/2026` |

---
---

# {{PROJECT}} — where to start

This folder is the handover from {{COACH}} to {{RECIPIENT}}: from now on, {{RECIPIENT}} steers the
rest of the project with their own AI tools, without {{COACH}} being available day to day.

**Before doing anything to the code**, follow the steps below, in order. They install no coding tool.
They set up the assistant that will then guide you step by step through everything else.

Nothing that follows happens in a terminal. It all happens in a web page or an application, with a
button to click.

## What is in this folder

| File | What it is for |
|---|---|
| `README.md` | this file, the getting started guide |
| `00-method-and-roles.md` | the working method, and the exact text to paste to create {{COPILOT_NAME}} |
| `01-phasing-and-checklist.md` | the project's main stages, once {{COPILOT_NAME}} is live |
| `02-context.md` | what is already settled, and what is still open |
| `03-stack-and-technical-decisions.md` | the technical instructions {{CODING_AI}} reads before writing any code |
| `handover.html` | **the visual overview**. Double-click it to open it in your browser |

💡 **If you read only one thing before starting**, open `handover.html`: objectives, setup,
dependencies, phasing and the cost of the tools, on a single page.

{{DOMAIN_DOCS_DIR}} (next to this folder) holds all the domain documentation for the current
application. {{COPILOT_NAME}} will go and read it; you have nothing to do with it for now.

## What you do **not** have to do

Three usual worries, cleared straight away:

- **You do not have to write up your requirements.** It is not your job to write what the application
  should do. {{COPILOT_NAME}} will ask you simple questions, one at a time, about your work rather
  than about screens or technology. It will play back what it understood, have you confirm it, and
  **it** will put it into shape. Your only job: read it and say "yes, that's it" or "no, actually…".
- **You have no paid account to open, and no card to hand over.** The hosting ({{HOSTING}}), the
  repository and the billing live on {{COACH}}'s accounts. They add you once as a collaborator, and
  you work on it alone from then on.
- **You do not have to ask permission every time.** Once the access is granted, you deploy and move
  forward without going back through {{COACH}}. They stay on the path for three things only: granting
  that access the first time, anything involving a payment, and making a repository public.

---

## Step 1 — Check your access

1. Open [{{REPO}}]({{REPO_URL}}).
2. If the page shows you the code (files, folders), you are set. Go to step 2.
3. If it shows "404 — page not found" or asks you to sign in, you do not have access yet. Tell
   {{COACH}}: it is theirs to invite you as a collaborator, and you will get an invitation email to
   accept.

Do the same check on [{{METHOD_REPO}}]({{METHOD_REPO_URL}}), the method template used to structure the
project. Same move if the access is missing.

Finally, check that you are a **collaborator on {{HOSTING}}**, where the application will go live: sign
in and see whether the project appears in your list. The account stays {{COACH}}'s. You are not
opening one, you are simply invited onto it.

**What you should see at the end**: both repository pages open and show a list of files, and the
project appears in your {{HOSTING}}.

💡 Those three invitations are **the only thing** {{COACH}} has to do for you at the start. Once they
are in place, you no longer need to ask them anything to work. And when a request genuinely has to go
to them, {{COPILOT_NAME}} will write it out ready to send. You will never have to improvise a request,
nor wait doing nothing: it will also tell you what to get on with meanwhile.

## Step 2 — Check that {{CODING_AI}} points at this repository

{{CODING_AI}} is the tool that will write the code. It is already connected to the {{REPO}} repository.

1. Open it and ask it to **resync with the repository** (the button or command that pulls the latest
   version from {{REPO_HOST}}).
2. Then ask it to list the contents of the `{{PACK_DIR}}` folder.

**What you should see at the end**: it names the files listed in the table above. If it cannot see
that folder, it is out of date: explicitly ask it to resync before going any further.

## Step 3 — Set up {{COPILOT_NAME}}, the AI that steers

This is the heart of the handover: an assistant configured with {{COACH}}'s method, which will now
guide you in their place. It does not write code. It frames, designs, reviews what {{CODING_AI}}
produces, and refuses to move on while a step is unfinished.

<!-- CONDITIONAL SECTION: the setup procedure for a "configured once and for all" assistant, of the
     Custom GPT kind. Replace it entirely if {{STEERING_AI}} is another kind:
       - a project space (Claude Project, ChatGPT Project) → create the project, paste the
         "Instructions" text into the project instructions, drop the files into its knowledge space;
       - a plain prompt to paste again → nothing to install; the recipient opens a fresh conversation
         and pastes the "Instructions" text as the first message, every time. Say that explicitly:
         it is the trap of this variant.
     In every case, keep the "What you should see at the end" and "Known trap" points. -->

> *Points 1 to 6 below apply if {{STEERING_AI}} is an **assistant configured once and for all**. If it
> is a project space or a plain prompt to paste again, this procedure is replaced. The rest of the
> step does not change.*

1. Go to [{{STEERING_AI_SETUP_URL}}]({{STEERING_AI_SETUP_URL}}), signed in with your {{AI_PLAN}}
   account.
2. Choose the **form-based** configuration rather than the guided conversational one: we are going to
   fill the fields directly, which is more reliable.
3. Open the `00-method-and-roles.md` file in this folder. It carries, ready to copy and paste, the
   **Name**, **Description**, **Instructions** and **Conversation starters** fields. Paste each into
   the matching field, **without changing anything**.
4. In the assistant's **capabilities**, turn on **web search**. Leave **code execution** and
   **integrations / actions** off: {{COPILOT_NAME}} does not write code, that is {{CODING_AI}}'s job.
5. In the **knowledge files** area, add:
   - every file in {{DOMAIN_DOCS_DIR}}
   - the four files `{{PACK_DIR}}00-method-and-roles.md`, `01-phasing-and-checklist.md`,
     `02-context.md` and `03-stack-and-technical-decisions.md`

   The easiest way to get them: in {{REPO_HOST}}, open each file and use the button that downloads the
   raw file; or ask {{CODING_AI}} to prepare them in a folder you drag and drop here.
6. Save, then set the sharing to **private / only me**. This assistant holds documentation internal to
   {{ORGANISATION}} and must not be public.

**What you should see at the end**: an assistant named "{{COPILOT_NAME}}" appears in your sidebar. Open
it and send a first message, for example:

```
We're starting {{PROJECT}}, frame the first step for me
```

If it answers by restating the frame of the step, the deliverables, and what is expected of it and of
you (see the step format described in `00-method-and-roles.md`), the handover has worked and you can
carry on with it from here.

⚠️ **Known trap**: a configured assistant **never resyncs itself** with the repository. If one of the
knowledge files changes later, the new version has to be downloaded and re-uploaded by hand.

## Step 4 — Open {{DIAGRAM_TOOL}}, for the diagrams

You will use it for the screen mockups and diagrams {{COPILOT_NAME}} asks you to approve.

1. Go to {{DIAGRAM_TOOL}}. Nothing to install, it works straight in the browser.
2. So that your diagrams survive from one session to the next, create a free account rather than
   staying as a guest.

**What you should see at the end**: a blank page with a drawing toolbar. That is it, and
{{COPILOT_NAME}} will explain how to use it when the time comes.

## Step 5 — Carry on with {{COPILOT_NAME}}

Once steps 1 to 4 are done, go back to the conversation with {{COPILOT_NAME}} and ask it to frame what
comes next. `01-phasing-and-checklist.md` lists the main stages it will walk you through one by one.
You do not need to read it in full now; it will guide you through it.

It will start by getting you to **talk about your work**: how things go today, who does what, what gets
stuck. Answer plainly, the way you would explain it to someone arriving. That is where it draws the
list of what has to be built, and it will have you read that list back before it settles on anything.

One step open at a time. That is the rule that stops the project sprawling in every direction.

---

*{{VERSION}} — {{DATE}}*
