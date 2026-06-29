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

## Human vs Agent Responsibilities

Experience extraction is a human decision, not an Agent close-out step.

- A human decides whether work produced a reusable lesson and when to trigger
  extraction. Humans are also responsible for spotting cross-target patterns,
  because those only become visible across many plans.
- An Agent's role is to assist, never to gate-keep:
  - surface candidate signals (a repeated failure, a contradicted rule, an
    unsafe shortcut, a validation gap) for a human to confirm;
  - when asked, draft a candidate lesson note that cites evidence and fills the
    template;
  - leave the accept / edit / reject decision to the human.

The reason is the same anti-self-evaluation principle the kernel applies to
quality gates. "Reusable", "repeated failure mode", and "applies to other
projects" have no deterministic boundary. If an Agent self-decided, every
target would either force a shallow lesson (turning this layer into a second
log) or miss patterns that only a human can see across work.

## Suggested Workflow

1. Let target plans and `plan/log.md` record facts first. Extraction is not
   part of target close-out.
2. A human reviews recent logs, failed plans, and repeated fixes and decides
   whether a lesson is worth extracting.
3. When the human asks, the Agent drafts a candidate lesson note with evidence.
4. The human accepts, edits, or rejects the candidate.
5. Cite the evidence: plan paths, log entries, commits, reports, or reviews.
6. Feed mature lessons back into `AGENTS.md`, templates, or validation checks.

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
