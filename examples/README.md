# Real cases

🔴 **Pointers, never copies.** A case copied in here drifts from its own repository within the week,
and then nobody knows which one is authoritative. Each entry says where to go and read it, and what
the case taught this template.

---

## The founding case: a non-technical director takes over a rebuild (25/08/2026)

**Where to read it**: the handover pack lives in the project's own repository, under `docs/refonte/`.
*(Private repository. The case is here for its method rather than its code, and the recipient is not
named: this template describes situations, not people.)*

**The situation**: an invoicing and stock application, in production, built by the coach. The coach
is no longer available. The company's director takes over the steering of a full rebuild onto a
different stack, with their own tools. They do not write code and do not want to, which is precisely
the situation this template addresses rather than a shortcoming.

**The setup chosen**: a Codex project already connected to the repository writes the code; a Custom
GPT created for the occasion holds the method and the ways out. The Custom GPT has **no** Git
access, and the recipient bridges the two by hand. That choice is deliberate: giving a Custom GPT
the illusion of repository access produces invented answers about its state.

**What this case taught the template**:

- The handover pack lives **in the project's repository**, not in a separate notes space. The
  recipient has already cloned it, so `git pull` then `git diff` is enough to show them what arrived.
- The question "why rebuild rather than evolve?" was written down nowhere. A rebuild decision with
  no written justification gets re-argued at every difficulty, and a project that gets re-argued is
  a project that stops. The template now requires that justification, and marks it `⚠️ À TRANCHER`
  when it is missing rather than inventing one.
- The security carried by the v1 infrastructure (Postgres row-level security) disappears when the
  stack changes. Any change of foundation has to list **what the foundation was providing for free**
  and now has to be reimplemented. It is the number one regression risk of a rebuild.
- The recipient's geography is not local colour: an unstable network and modest devices translate
  into verifiable constraints on the code.
- Naming the first post-rebuild feature **in advance** heads off the "could we just add this?"
  conversation during the rebuild itself.
- The first instinct, when the hosting accounts belong to the coach, is to invent a standing ritual
  for requesting things. That was a mistake: it puts the coach back on the critical path at exactly
  the moment they are no longer available. The correction, **hand the access over once and keep only
  billing and the switch to public**, became a rule of the template.
- Requirements gathering had not been assigned to anyone. With no explicit owner it falls by default
  on the recipient, which is not their job, and the coaching then degrades into order-taking.
