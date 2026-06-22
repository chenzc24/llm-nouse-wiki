# Plan Directory

The `plan/` directory stores implementation intent and factual maintenance
history. It exists so Agents do not make unbounded, unowned, or unverifiable
changes.

## Target Plans

Create a target plan before editing tracked files.

Default path:

```text
plan/<date-goal-slug>/plan.md
```

Example:

```text
plan/2026-06-22-add-search-index/plan.md
```

Each target plan should include:

- goal
- dirty-state note
- owned files or directories
- read-only files or directories
- expected work
- validation steps
- commit intent or commit policy

Use `plan/target-plan.template.md` as the starter format.

## Dirty Worktree Handling

A dirty worktree does not automatically block unrelated work.

Proceed only when:

- dirty files are unrelated to the current target
- dirty files do not overlap the target's owned files
- dirty files do not change shared contracts or dependencies the target relies
  on
- the target plan records the dirty-state decision

Stop and ask for coordination when:

- a dirty file overlaps the target's owned files
- ownership of the dirty file is unclear
- a dirty shared contract may affect this target
- the current task would need to edit or stage someone else's dirty file

## Maintenance Log

`plan/log.md` records accepted project-level maintenance history.

Each entry should record:

- date
- target
- changed areas
- validation performed
- commit status

Keep the log factual. It should answer what happened, not pretend every task
produced a reusable lesson.

## Experience Extraction

When one or more plans or logs reveal a transferable lesson, extract it into
`docs/experience/`.

Good triggers:

- the same failure happened more than once
- a rule changed because reality contradicted the original plan
- a validation command caught an issue that model review missed
- a coordination rule prevented or failed to prevent conflicting edits
- a shortcut saved time and remained safe

Experience notes should cite the relevant plans, logs, commits, reports, or
reviews.

## Relationship To Git

Plans and logs do not replace Git.

Plans explain intent before work starts. Logs explain factual outcomes after
work finishes. Git records the actual repository state.

A complete target should normally end with:

1. validation
2. log update
3. intended files staged
4. commit
5. push according to project policy
