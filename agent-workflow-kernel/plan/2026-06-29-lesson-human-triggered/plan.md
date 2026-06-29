# Lesson Human-Triggered Plan

## Goal

Correct the lesson layer's design so it honestly reflects that experience
extraction is a human judgment, not an agent self-evaluation. Today the
AGENTS.md wording uses soft conditionals ("if the target produced a reusable
lesson", "when work reveals"), which implies an agent can detect a lesson at
target close. That is not reliable: lesson detection is a judgment call agents
cannot make deterministically.

The intended split is:

- Humans decide whether work produced a reusable lesson and trigger
  extraction.
- Agents assist extraction by drafting, citing evidence, and filling the
  lesson template — but do not gate-keep whether a lesson exists.

This is the same anti-self-evaluation principle the kernel already applies to
quality gates.

## Dirty-State Note

```text
## main...origin/main
```

The worktree is clean.

## Owned Files

- `agent-workflow-kernel/AGENTS.md`
- `agent-workflow-kernel/README.md`
- `agent-workflow-kernel/docs/experience/README.md`
- `agent-workflow-kernel/plan/target-plan.template.md`
- `agent-workflow-kernel/plan/2026-06-29-lesson-human-triggered/plan.md`
- `agent-workflow-kernel/plan/log.md`

## Read-Only Files

- `agent-workflow-kernel/plan/README.md` (only touched if the mainline figure
  is inconsistent after edits; otherwise not edited)

## Shared Dependencies

- None. The lesson layer is self-contained prose and templates.

## Expected Work

1. AGENTS.md:
   - Replace the conditional "if the target produced a reusable lesson" with
     an explicit human-triggers / agent-assists split.
   - Add a short note that an agent should never decide on its own that a
     lesson is worth extracting; it may only propose a candidate lesson when
     asked, or flag a suspected pattern for a human to confirm.
   - Keep the "log is not experience" boundary intact.
2. docs/experience/README.md:
   - Add a "Human vs Agent Responsibilities" section.
   - Make explicit that triggering extraction is a human call and that an
     agent's role is drafting, evidence citation, and template filling.
3. plan/target-plan.template.md:
   - Reframe the "Experience Trigger" field. It is not an agent self-check; it
     is a signal a human can read when deciding whether to ask for extraction.
     Rename and reword accordingly.
4. README.md:
   - Align the mainline figure and prose so "experience" is consistently
     optional and explicitly human-triggered, not part of every commit's
     automatic close-out.

## Validation

- `git diff --check`
- `git status --short --branch`
- Targeted `rg` for:
  - residual "if the target produced a reusable lesson" / "when work reveals"
    conditionals that imply agent self-detection
  - "human" and "agent" responsibility split in experience docs
  - optional / human-triggered language around the experience layer

## Commit Intent

```text
Make lesson extraction human-triggered, agent-assisted
```
