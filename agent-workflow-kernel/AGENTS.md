# Agent Working Rules

This repository uses a plan-log-experience workflow for Agent-assisted work.
Agents should treat the repository as an engineering project: bounded targets,
explicit ownership, validated changes, durable logs, and periodic experience
extraction.

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
4. If the target produced a reusable lesson, add or update an experience note
   under `docs/experience/`.
5. Review the diff.
6. Stage only the intended files.
7. Commit and push according to the project's branch policy.

## Plan-Log-Experience Mainline

The portable workflow is:

```text
target plan
-> bounded implementation
-> validation
-> factual log entry
-> optional experience note
-> commit
```

The log is not the experience layer. A log records what happened. An experience
note extracts a reusable judgment from one or more logs, commits, reviews, or
failed attempts.

Create or update an experience note when work reveals:

- a repeated failure mode
- a rule that should change
- a process shortcut that proved unsafe
- a validation gap
- a reusable coordination pattern
- a project assumption that was confirmed or rejected by evidence

Experience notes should cite the plans, logs, commits, or reports that support
the lesson.

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
- If a completed plan contains a reusable lesson, extract that lesson before
  archiving the plan.
