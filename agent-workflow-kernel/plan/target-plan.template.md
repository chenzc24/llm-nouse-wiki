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

## Experience Signal (for human review)

This field is not an Agent self-check. It is a signal a human can read later
when deciding whether to ask for a lesson from this target.

Note any candidate signal that appeared during work, such as a repeated
failure, a contradicted rule, an unsafe shortcut, or a validation gap. Leave
empty for routine work. An Agent may flag a suspected signal here, but the
decision to extract a lesson is a human call.

## Commit Intent

Commit as:

```text
<commit message>
```
