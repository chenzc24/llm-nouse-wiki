# Experience Notes

`docs/experience/` is for reusable project lessons extracted from plans, logs,
commits, reviews, validation reports, and failed attempts.

It is not a second maintenance log.

## What Counts As Experience

A note belongs here when it explains a transferable judgment:

- what assumption was tested
- what happened
- what evidence supports the conclusion
- what rule, template, validation command, or habit should change
- where the lesson does and does not apply

## What Does Not Belong Here

- a raw list of changed files
- a copied commit message
- a daily status update
- a validation transcript without interpretation
- a broad principle with no evidence

Those belong in `plan/log.md`, commit history, or a project status report.

## Suggested Workflow

1. Let target plans and `plan/log.md` record facts first.
2. Periodically review recent logs, failed plans, and repeated fixes.
3. Extract only lessons that should influence future work.
4. Cite the evidence: plan paths, log entries, commits, reports, or reviews.
5. Feed mature lessons back into `AGENTS.md`, templates, or validation checks.

## File Naming

Use short, dated names when the lesson is tied to a concrete project event:

```text
YYYY-MM-DD-short-lesson-title.md
```

Use stable names for evergreen practices:

```text
plan-log-experience-loop.md
dirty-worktree-ownership.md
validation-before-confidence.md
```

Use `lesson.template.md` as the starter format.
