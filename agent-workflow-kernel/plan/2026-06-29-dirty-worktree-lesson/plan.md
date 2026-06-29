# Dirty Worktree Lesson Example Plan

## Goal

Fill the first real example lesson in `docs/experience/` so the experience
layer is demonstrated by a real case, not only by an empty template. This
closes the kernel's gap 2: adopters currently have no sample to imitate, so
the "not a second log" rule is a slogan with nothing to compare against.

The example is drawn from the parent repository's real history: the
2026-06-03 decision to replace a strict clean-worktree requirement with a
dirty-state audit. It has a complete evidence chain (plan + log + commit),
which makes the Evidence field honest rather than fabricated.

This lesson also serves a second purpose: by writing it correctly, it
demonstrates the direction we clarified last round — Evidence points to
events (log/plan/commit), and "Rule Or Workflow Change" is an output (where
the lesson reflowed), not a reference back from the rule.

## Dirty-State Note

```text
## main...origin/main
 M agent-workflow-kernel/AGENTS.md
 M agent-workflow-kernel/README.md
 M agent-workflow-kernel/docs/experience/README.md
 M agent-workflow-kernel/plan/README.md
 M agent-workflow-kernel/plan/log.md
 M agent-workflow-kernel/plan/target-plan.template.md
?? agent-workflow-kernel/plan/2026-06-29-lesson-human-triggered/
```

All dirty paths belong to the previous target
(`2026-06-29-lesson-human-triggered`, awaiting commit). None overlap this
target's owned files. Proceeding per the dirty-state audit rule; the previous
target should be committed first, but its presence does not block this one.

## Owned Files

- `agent-workflow-kernel/docs/experience/dirty-worktree-ownership.md`
- `agent-workflow-kernel/plan/2026-06-29-dirty-worktree-lesson/plan.md`
- `agent-workflow-kernel/plan/log.md`

## Read-Only Files

- `agent-workflow-kernel/AGENTS.md`
- `agent-workflow-kernel/docs/experience/README.md`
- `agent-workflow-kernel/docs/experience/lesson.template.md`
- everything outside `agent-workflow-kernel/`

## Shared Dependencies

- None. This is a single new example file plus its own plan and log entry.

## Expected Work

1. Create `docs/experience/dirty-worktree-ownership.md` following
   `lesson.template.md`.
2. Fill every section from the real 2026-06-03 dirty-worktree case:
   - Evidence cites the real plan path, log entries, and commit `bd1518d`.
   - Original Assumption states the prior clean-worktree requirement.
   - What Happened states the parallel-work blocking.
   - Interpretation explains why "clean" was the wrong gate.
   - Rule Or Workflow Change records that this already reflowed into
     `AGENTS.md §Operating Discipline` (as the dirty-state audit rule), so the
     field reads as an output, not a reverse reference.
   - Transferable Principle and Limits state where it does and does not apply.
3. Keep it as a lesson (judgment + evidence + limits), not a log entry. No
   "today I changed files X, Y" narration.
4. Do not edit AGENTS.md or the template; this target only adds an example.

## Validation

- `git diff --check`
- `git status --short --branch`
- Targeted `rg` confirming the new file:
  - cites commit `bd1518d` and the real plan path
  - contains `Limits` and `Transferable Principle` sections
  - is referenced nowhere as if it were a reverse-index target (it is not)

## Commit Intent

```text
Add dirty-worktree example lesson
```
