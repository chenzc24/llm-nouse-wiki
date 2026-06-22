# Target Title

## Goal

State the concrete objective.

## Dirty-State Note

Start state from `git status --short --branch`:

```text
<paste status>
```

State whether the worktree is clean or why unrelated dirty files are safe to
leave untouched.

## Owned Files

- `<paths this target may edit>`

## Read-Only Files

- `<paths this target may inspect but not edit>`

## Shared Dependencies

- `<shared contracts, generated artifacts, APIs, docs, or decisions this work
  depends on>`

## Expected Work

1. `<step>`
2. `<step>`
3. `<step>`

## Validation

- `git diff --check`
- `git status --short --branch`
- `<project-specific command>`

## Experience Trigger

State whether this target is likely to produce a reusable lesson. If yes,
identify the expected `docs/experience/` note.

## Commit Intent

Commit as:

```text
<commit message>
```
