# Lesson: Dirty Worktree Is an Ownership Question, Not a Cleanliness Question

## Summary

A dirty worktree should not block work by default. Block only when a dirty
path overlaps the current target's owned files, ownership is unclear, or a
dirty shared contract changes something the target depends on. Treat
"cleanliness" as the wrong gate; the real gate is ownership overlap.

## Background

Multi-agent and parallel work in a Git-first repository. An earlier policy
required a fully clean worktree before any target could start, to avoid mixing
unrelated changes.

## Evidence

- Plan: `plan/users/chenzc24/2026-06-03-relax-dirty-worktree-policy/plan.md`
  (parent repository)
- Commit: `bd1518d Relax dirty worktree policy for parallel work`
- Maintenance log entries in the parent repository's `plan/log.md` and
  `plan/users/chenzc24/log.md` dated 2026-06-03.

## Original Assumption

A clean worktree is the safe precondition for any new target. If anything is
already modified, the new target's edits could be confused with the existing
dirty changes, so work should not begin until the worktree is fully clean.

## What Happened

With multiple workers and agents operating in parallel, the clean-worktree
requirement turned into a serialization point. One worker's unfinished target
blocked another worker's unrelated target, because the presence of any dirty
file — even one touching a completely different part of the repository — was
treated as a universal stop signal. The blocking was not protecting anything
real in most cases; the dirty files and the new target simply did not overlap.

## Interpretation

The clean-worktree rule was solving the wrong problem. The actual risk is not
"dirtiness" in general; it is specifically:

- a dirty file that the current target also needs to edit (edit conflict),
- a dirty file whose ownership is unclear (who resolves it?),
- a dirty shared contract that the current target depends on (silent
  dependency drift).

If none of those hold, a dirty file elsewhere in the repo is irrelevant to the
current target. Requiring global cleanliness conflates "the repository is
tidy" with "this target is safe to start", and the two are unrelated. The
correct gate is an ownership-overlap audit, not a cleanliness check.

## Rule Or Workflow Change

This lesson has already reflowed into the kernel as a rule. It is not a
pending proposal:

- `AGENTS.md` §Operating Discipline step 2 encodes the dirty-state audit.
- `plan/target-plan.template.md` carries a `Dirty-State Note` field so each
  target records its audit decision when the worktree is not clean.

The direction here is lesson → rule (output). The rule does not and should not
reference this lesson back; the rule's authority comes from being the rule,
not from carrying its own rationale inline. To understand why, read this
lesson; to execute, read the rule.

## Transferable Principle

When a safety rule is phrased as a global condition ("everything must be
clean"), check whether the actual risk is narrower ("this specific thing must
not overlap"). Broad preconditions are easy to state and easy to enforce, but
they serialize work that has no real conflict. Narrow, ownership-based gates
allow parallelism and still catch the cases that actually matter.

This applies beyond worktree state: the same pattern shows up in branch
policies, review gates, and deployment locks that block globally when only a
subset of changes are risky.

## Limits

This lesson does not apply when:

- The target genuinely needs to edit a file that is already dirty — stop and
  coordinate.
- Ownership of a dirty file is unclear — do not proceed on assumption.
- A dirty shared contract (schema, API, config) may change behavior the target
  relies on — stop, because the dependency is no longer what the target was
  planned against.
- The repository has a release freeze or integration window where global
  cleanliness is a real requirement, independent of any single target.

A dirty worktree is safe to ignore only when it is provably unrelated to the
current target's owned files and shared dependencies.

## Follow-Up

- None. This lesson is recorded as a worked example; the rule it supports is
  already in place.
