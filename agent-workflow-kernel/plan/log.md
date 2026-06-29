# Maintenance Log

This log records accepted project maintenance history.

Use concise entries:

```text
## YYYY-MM-DD - Target title

- Target: what the work set out to do.
- Changed areas: files, directories, or subsystems changed.
- Validation: commands or review performed.
- Commit status: committed, ready to commit, not committed, or blocked.
```

Keep reusable lessons in `docs/experience/`, not in this log.

## 2026-06-29 - Make lesson extraction human-triggered, agent-assisted

- Target: correct the lesson layer so it honestly reflects that experience
  extraction is a human judgment, not an Agent self-evaluation. The previous
  wording used soft conditionals ("if the target produced a reusable lesson"),
  which implied an Agent could detect a lesson at target close.
- Changed areas: rewrote the experience wording in `AGENTS.md` (After Work,
  Plan-Log-Experience Mainline, Plan Hygiene), `README.md` (two-layer mainline
  figure), `docs/experience/README.md` (new Human vs Agent Responsibilities
  section), `plan/README.md` (Experience Extraction), and renamed the
  target-plan `Experience Trigger` field to `Experience Signal (for human
  review)`.
- Design review: the kernel now explicitly splits responsibilities — humans
  decide when a lesson is worth extracting; Agents assist by surfacing signals
  and drafting candidate notes, but never gate-keep. This matches the existing
  anti-self-evaluation principle.
- Validation: `git diff --check` passed with only Windows line-ending warnings;
  `git status --short --branch` showed only the intended files; targeted `rg`
  confirmed no residual "if the target produced" / "when work reveals" /
  "periodic experience" conditionals in rules, READMEs, or templates.
- Commit status: ready to commit as `Make lesson extraction human-triggered,
  agent-assisted`.

## 2026-06-29 - Add dirty-worktree example lesson

- Target: fill the first real example lesson in `docs/experience/` so the
  experience layer is demonstrated by a real case, not only an empty template.
- Changed areas: added
  `agent-workflow-kernel/docs/experience/dirty-worktree-ownership.md`; also
  removed a trailing blank line in `plan/log.md` left by the previous target.
- Design review: the lesson is drawn from the parent repository's real
  2026-06-03 dirty-worktree decision, so its Evidence field cites a real plan,
  log, and commit (`bd1518d`). It demonstrates the direction clarified last
  round: Evidence points to events, and "Rule Or Workflow Change" records
  where the lesson already reflowed (output), not a reverse reference.
- Validation: `git diff --check` passed; `git status --short --branch` showed
  only this target's files plus the previous target's pending changes, with no
  overlap; targeted `rg` confirmed the lesson cites `bd1518d`, the real plan
  path, and contains `Limits` and `Transferable Principle` sections.
- Commit status: ready to commit as `Add dirty-worktree example lesson`.