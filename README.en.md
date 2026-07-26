<div align="center">

<a href="README.md">简体中文</a> | English

<h3><s>The Legacy Project Exorcism Manual</s></h3>

<h1>Project Canon · Agent Skill</h1>

<p><strong>Agent Skill for long-running AI coding projects: maintain one source of truth, reconcile docs with code, track decisions, archive stale plans, and resume after context loss.</strong></p>

<p>Keep one traceable source of truth for project decisions, delivery status, evidence, and continuation.</p>

</div>

> **Help AI remember what the project actually decided—not merely what the last conversation said.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent-Skill-5B5BD6)](SKILL.md)
[![Language](https://img.shields.io/badge/docs-English-blue.svg)](README.en.md)

Working with AI on a project for weeks, you often end up with:

- three documents all called “final plan”;
- AI not knowing which version is the real one;
- abandoned designs coming back to life in the next chat;
- code, plans, and verification status pretending to agree;
- everything reopening for discussion because you switched to a new session.

**Project Canon** is a governance Skill for long-running AI coding projects. It helps an Agent locate the project's existing authoritative entry points, separate proposals from accepted decisions, changes, delivery status, and evidence, and safely resume work after context loss.

It does not invent truth for the project. It maintains and traces facts the project has actually accepted.

## What it solves

- Several documents all claim to be the latest plan.
- Ideas from chat are silently promoted into formal decisions.
- “Accepted,” “implemented,” and “verified” are treated as the same status.
- Code reality conflicts with the target design and silently overwrites it.
- Reviewed historical plans remain scattered around the workspace.
- A new session, model, or Agent reopens decisions that were already settled.
- AI creates more directories, indexes, and duplicate documents in the name of organization.

Project Canon keeps the project able to answer:

```text
What has been accepted?
What is still open?
Why was this choice made?
What is the current change supposed to do?
What has actually been implemented?
Where is the evidence?
Where should work resume?
```

## Four operating modes

| Mode | Example request | Default behavior |
| --- | --- | --- |
| Audit | “Which plan is currently authoritative?” | Read-only inspection of authority, conflicts, duplicates, links, and status |
| Takeover | “Organize this existing project” | Classify files and provide a file-level Preview before migration |
| Maintain | “Write this decision back to the project” | Reuse the existing structure and minimally update the authoritative location |
| Resume | “Continue the previous work” | Re-read project entry points, active changes, workspace state, and fresh verification |

> Audits are read-only by default. Takeovers begin with a Preview. Writes require authorization.

## Before and after

| Without Project Canon | With Project Canon |
| --- | --- |
| Multiple "final" plans compete for authority | One current plan links to decisions, changes, and evidence |
| AI resumes from chat memory | AI re-reads the project's actual state each time |
| Stale documents resurface as truth | Finished materials are archived and mapped |
| "Implemented" is confused with "verified" | Each status has its own location and evidence |
| Every new session repeats old decisions | Existing decisions are preserved and auditable |

## Core model

Project Canon does not impose fixed directory names. It requires these responsibilities to be identifiable:

| Responsibility | Question it answers | Must not contain |
| --- | --- | --- |
| Current | What target has been accepted? | Delivery progress, temporary tests, unconfirmed proposals |
| Proposal | What is still being discussed? | Effective target design |
| Decision | Why was this option chosen? | Full plan copies or development logs |
| Change | What is this approved change intended to alter? | Daily progress or the entire future roadmap |
| Delivery | What has actually been implemented and verified? | Product or architecture target definitions |
| Evidence | Where did a conclusion or acceptance claim come from? | Conclusions promoted automatically into current truth |

The most important boundary is:

```text
Accepted design ≠ Implemented code ≠ Passed verification ≠ Proven real-world use
```

## Safe writeback workflow

```text
Discover local authority
→ Read the relevant material completely
→ Separate confirmations, proposals, advice, external claims, and verification evidence
→ Compare them with the current plan and existing decisions
→ Produce a writeback Preview
→ Obtain user confirmation
→ Apply the smallest change to authoritative locations
→ Update source mappings
→ Handle source files using the selected disposition mode
→ Recheck links, status, and unique authority
```

The Preview separates:

1. **Content writeback:** which conclusions will be written to which files and sections.
2. **File disposition:** whether to use conservative organization or archive migration, and the exact scope.

### Two file-disposition modes

**Conservative organization**

- Establish or update Current, Decision, Change, Delivery, and source mappings.
- Leave source materials in their original locations.
- Best when the user only needs an authoritative entry point or the project is changing rapidly.

**Archive migration**

- Move processed materials into the project's archive after content extraction and mapping.
- Best for “organize and archive” tasks and for cleaning scattered historical plans.
- Supports either file-by-file moves or an explicitly approved historical source bundle.

A historical prototype, design deliverable, or validation bundle may contain HTML, CSS, scripts, JSON, images, and fonts. Project Canon does not classify material by extension alone. It checks lifecycle, runtime entry points, current references, and replacement relationships. The archived scope must match the recorded source scope.

Source materials are not deleted by default.

## Local rules come first

Project Canon follows one simple rule:

> **Respect existing project rules first. Propose the minimum necessary structure only when rules are missing.**

It first reads applicable `AGENTS.md` files, entry-point READMEs, documentation rules, current delivery entry points, and version-control state.

Only a long-running, multi-stage project with formal changes and evidence-tracing needs should consider a structured profile such as:

```text
<canon-root>/
├─ README.md
├─ current/
├─ changes/
├─ delivery/
├─ decisions/
└─ evidence/
```

This is a reference profile, not a mandatory migration target.

## Quick start

Clone the repository into an Agent Skills directory that supports `SKILL.md`:

```bash
git clone https://github.com/gloria2creator/project-canon.git \
  <your-agent-skills-directory>/project-canon
```

Then invoke it explicitly:

```text
Use $project-canon to audit this project.
Identify the current authoritative plan, active work, conflicts, and duplicates.
Produce a Preview only. Do not modify files.
```

Or:

```text
Use $project-canon to take over this project's planning documents.
Use archive migration. First list the proposed content writeback and file-move scope,
then wait for my confirmation.
```

## Example prompts

### Find the current authoritative plan

```text
Use $project-canon to determine which plan is currently authoritative.
Validate declarations, links, local terminology, and adoption evidence.
Do not rely only on modification time. Audit only; do not fix anything.
```

### Absorb meeting notes or a historical plan

```text
Use $project-canon to review this material.
Separate accepted conclusions, proposals, conflicts, facts requiring verification,
and content with no long-term value. Produce a writeback Preview with exact targets.
```

### Organize and archive materials

```text
Use $project-canon to organize and archive these materials.
Verify that every source has been extracted and mapped.
For a source bundle, record current references, replacement relationships,
and the complete archive scope. Do not delete anything.
```

### Resume after context loss

```text
Use $project-canon to restore the current project state.
Re-read project rules, Current, the active Change, Delivery, Git state,
and fresh verification. Do not continue from chat memory.
```

### Reconcile documentation and code

```text
Use $project-canon to reconcile the current plan, delivery records, and code reality.
Report authority conflicts, stale status, traceability gaps, format drift,
and unstable snapshots separately. Do not silently choose code or docs as correct.
```

## Design principles

1. **Local rules first:** reuse existing directories, naming, numbering, and status values.
2. **Read-only first:** audits, diagnostics, and reports do not modify files by default.
3. **Preview first:** explain the scope before writing, moving, archiving, or deleting.
4. **Separate authorization:** adopting rules, accepting content, selecting the current Gate, and authorizing file disposition are distinct.
5. **Unique authority:** one primary location per conclusion; other files link to it.
6. **Fresh evidence:** historical tests do not prove that the current workspace still passes.
7. **Idempotence:** repeated organization must not create duplicate Decisions, Changes, or archive copies.
8. **Minimum governance:** do not prebuild a complete system for hypothetical future needs.

## What it is not

Project Canon is not:

- a Markdown beautifier;
- a one-shot cleaner for hundreds of historical files;
- a replacement for project management, requirements management, or version control;
- a script that forces every project into a fixed directory layout;
- a tool that declares the latest modified file authoritative;
- an autonomous Agent that decides the formal plan without confirmation.

For large-scale historical document cleanup, use a dedicated document-curation workflow first, then connect the stable conclusions to Project Canon.

## Repository structure

```text
project-canon/
├─ README.md
├─ README.en.md
├─ SKILL.md
├─ agents/
│  └─ openai.yaml
├─ references/
│  ├─ adoption-and-migration.md
│  ├─ authority-and-routing.md
│  ├─ source-intake-and-archive.md
│  ├─ audit-and-continuation.md
│  └─ structured-governance-profile.md
└─ assets/
   └─ templates/
      ├─ intake-preview.md
      ├─ decision.md
      ├─ change.md
      └─ delivery.md
```

- [`SKILL.md`](SKILL.md): core execution workflow for the Agent;
- [`references/adoption-and-migration.md`](references/adoption-and-migration.md): authorization boundaries, disposition modes, and migration gates;
- [`references/authority-and-routing.md`](references/authority-and-routing.md): authority roles, conflict resolution, and confirmation records;
- [`references/source-intake-and-archive.md`](references/source-intake-and-archive.md): source intake, source bundles, and safe archiving;
- [`references/audit-and-continuation.md`](references/audit-and-continuation.md): audits, status reconciliation, and continuation;
- [`references/structured-governance-profile.md`](references/structured-governance-profile.md): optional governance profile for complex projects;
- [`assets/templates/`](assets/templates/): minimal templates for projects without existing formats.

## Who it is for

- Individual developers using Codex, Claude Code, Cursor, or other coding Agents over long periods;
- small teams maintaining product, experience, architecture, and implementation plans together;
- projects that frequently cross sessions, models, or Agents;
- repositories with accumulated historical plans that need safe absorption and archiving;
- teams that want a reliable project-fact layer without heavyweight process.

## Contributing

Issues and pull requests are welcome, especially for real authority-conflict cases, adaptations to different project structures, and safer lightweight governance patterns.

Please follow Project Canon's own principle when contributing: **solve real problems without adding complexity for hypothetical future needs.**

## License

[MIT](LICENSE)

---

<p align="center">
  <strong>Project Canon</strong><br>
  One project. One traceable truth. Many agents.
</p>
