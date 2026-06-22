# Agent Workflow Kernel

This directory contains a portable Agent workflow kernel. It is meant to be
copied into a project that wants Agent-assisted work to be planned, auditable,
and able to produce reusable project experience.

The mainline is:

```text
plan
-> implementation
-> validation
-> log
-> experience
-> commit
```

## What This Kernel Provides

- `AGENTS.md`: repository-level Agent working rules
- `plan/README.md`: how target plans and logs work
- `plan/target-plan.template.md`: a starter plan format
- `plan/log.md`: factual maintenance log starter
- `docs/experience/README.md`: how to extract reusable lessons
- `docs/experience/lesson.template.md`: a starter experience note format

## What It Does Not Provide

This kernel is not a project-management system, a note-taking app, or a
complete development methodology. It gives Agents and humans a small shared
protocol for bounded work:

- plan before editing
- declare file ownership
- validate changes
- record factual outcomes
- extract reusable lessons when the work teaches something

Project-specific repositories should add their own domain rules, validation
commands, branch policy, release policy, and review expectations.

## How To Adopt

1. Copy this directory's contents into a new or existing repository.
2. Keep `AGENTS.md` at the repository root, or merge its generic rules into the
   project's existing `AGENTS.md`.
3. Keep `plan/README.md`, `plan/log.md`, and the target-plan template.
4. Keep `docs/experience/README.md` and the lesson template if the project
   wants reusable experience notes.
5. Add project-specific validation commands and branch policy.

## Core Distinction

A plan is intent before work.

A log is a factual record after work.

An experience note is a reusable judgment extracted from evidence.

Do not call raw logs "experience" until they explain a transferable pattern,
failure mode, rule change, or decision principle.
