# Agent Workflow Kernel Plan

## Goal

Create a repository-local `agent-workflow-kernel/` extraction that captures the
portable plan-log-experience workflow separately from the LLM Wiki-specific
rules in the root `AGENTS.md`.

## Dirty-State Note

Start state from `git status --short --branch`:

```text
## main...origin/main
```

The worktree is clean.

## Owned Files

- `agent-workflow-kernel/**`
- `README.md`
- `plan/users/chenzc24/2026-06-22-agent-workflow-kernel/plan.md`
- `plan/users/chenzc24/log.md`
- `plan/log.md`

## Read-Only Files

- `AGENTS.md`
- `rules/**`
- `skills/**`
- `templates/**`
- `contracts/**`
- `llm_wiki_tools/**`
- `tests/**`
- `llm_wiki/**`
- `MinerU/**`

## Expected Work

1. Add `agent-workflow-kernel/AGENTS.md` as a generic Agent working protocol.
2. Add a kernel `README.md` that explains the transferable plan-log-experience
   mainline.
3. Add `plan/` guidance and a target-plan template for adopters.
4. Add `docs/experience/` guidance and a lesson template that turns logs into
   reusable experience.
5. Add a concise root README pointer to the extracted kernel.
6. Update personal and global logs.

## Validation

- `git diff --check`
- targeted `rg` for kernel path, plan-log-experience language, and removed LLM
  Wiki-specific terms from the extracted kernel
- `git status --short --branch`

## Commit Intent

Commit as:

```text
Extract agent workflow kernel
```
