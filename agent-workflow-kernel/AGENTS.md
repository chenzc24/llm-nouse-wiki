# Agent Working Rules

This repository uses a plan-log-experience workflow for Agent-assisted work.
Agents should treat the repository as an engineering project: bounded targets,
explicit ownership, validated changes, and durable logs. Reusable experience
is extracted separately, and only when a human decides it is worth extracting.

## Operating Discipline

Before starting any single target:

1. Run `git status --short --branch` from the repository root.
2. Perform a dirty-state audit:
   - If the worktree is clean, proceed normally.
   - If the worktree is dirty, identify the changed paths and whether they
     belong to the current target, the user, another co-worker, or a previous
     task.
   - Do not require a fully clean repository when dirty paths are unrelated to
     the current target.
   - Stop before editing if dirty paths overlap the current target's owned
     files, ownership is unclear, or a dirty shared file changes a contract the
     current target depends on.
   - If proceeding with unrelated dirty files present, record that decision in
     the target plan.
3. Identify the target owner, goal, expected files, and validation surface.
4. Read project-specific entry documents when they exist, such as `README.md`,
   local design notes, or domain-specific `AGENTS.md` extensions.

## Before Editing

Create or update a target-specific plan before editing tracked files.

The default location is:

```text
plan/<date-goal-slug>/plan.md
```

If the project uses user namespaces or shared integration namespaces, follow
the project's local `plan/README.md`.

The plan must state:

- goal
- expected changed files
- owned files or directories
- read-only files or directories
- shared-contract dependencies, if any
- dirty-state note, if the worktree was not clean at start
- implementation steps
- validation steps
- intended commit message or commit policy

Do not edit files outside the owned set without updating the plan first.

## During Work

Keep the target bounded.

- Prefer small, reviewable changes over broad mixed edits.
- Keep unrelated cleanup out of the current target.
- Treat shared contracts, generated artifacts, and user-owned work as protected
  unless the plan explicitly claims them.
- When a new risk or dependency appears, update the target plan before changing
  scope.
- Prefer deterministic validation over model-only judgment.
- Record unresolved questions in the plan or a review note instead of hiding
  them in chat.

## After Work

Before considering the target complete:

1. Run the validation listed in the target plan.
2. At minimum, run `git diff --check` and `git status --short --branch`.
3. Update `plan/log.md` with a factual maintenance record:
   - target
   - changed areas
   - validation performed
   - commit status
4. Review the diff.
5. Stage only the intended files.
6. Commit and push according to the project's branch policy.
7. Experience extraction is not an automatic close-out step. An Agent must not
   decide on its own that a reusable lesson exists. When a human asks for a
   lesson from this work, draft a candidate note under `docs/experience/` and
   cite the supporting plans, logs, or commits; let the human accept, edit, or
   reject it.

## Plan-Log-Experience Mainline

The portable workflow has two layers:

- A hard, automatic per-target loop:

```text
target plan
-> bounded implementation
-> validation
-> factual log entry
-> commit
```

- A soft, human-triggered experience layer that runs across targets:

```text
human reviews recent plans, logs, or failures
-> human decides whether work produced a reusable lesson
-> Agent drafts a candidate lesson note (evidence, interpretation, limits)
-> human accepts, edits, or rejects
-> accepted lesson may later feed back into AGENTS.md or a template
```

The log is not the experience layer. A log records what happened. An experience
note extracts a reusable judgment from one or more logs, commits, reviews, or
failed attempts.

Deciding whether something is a reusable lesson is a judgment call. Agents
cannot make it reliably, because "reusable", "repeated failure mode", and
"applies to other projects" have no deterministic boundary. If an Agent
self-decided, the experience layer would drift back into being a second log:
every target would produce a forced lesson, or real cross-target patterns
would be missed.

Therefore:

- A human decides when to trigger experience extraction.
- An Agent's role is to assist: surface candidate signals, draft notes that
  cite evidence, and fill the lesson template. An Agent should never gate-keep
  whether a lesson is worth extracting on its own.
- Candidate signals an Agent may flag for a human (without asserting a lesson)
  include: a repeated failure mode, a rule that reality contradicted, an unsafe
  shortcut, a validation gap, a reusable coordination pattern, or an assumption
  confirmed or rejected by evidence.

This is the same anti-self-evaluation principle the kernel applies to quality
gates: do not let a model's own confidence be the only judge of whether a
judgment holds.

## Boundary Rules

- Do not mix unrelated targets in one plan, log entry, or commit.
- Do not mix reusable workflow changes with project-specific artifact changes
  unless the plan explicitly explains why they must land together.
- Do not treat a passing model review as the only quality gate when a
  deterministic check or human review path is available.
- Do not delete unresolved plans or open review notes merely to make the
  repository look clean.

## Plan Hygiene

Keep `plan/` useful.

- Completed detailed plans may be summarized into `plan/log.md` and archived or
  removed according to project policy.
- Failed, blocked, or unresolved plans should remain visible until the work is
  finished, superseded, or explicitly abandoned.
- Before archiving a completed plan, flag it for human review if it may contain
  a reusable lesson. Do not archive a plan that still carries an un-extracted
  lesson until a human has decided whether to extract it.
