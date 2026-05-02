# llmdoc Index

This tree records project memory for agents working on `thuthesis2e`.

`thuthesis2e` is the stable 2e reference and regression oracle for the
LaTeX3 rewrite. It should stay compatible with upstream ThuThesis unless a
branch is explicitly marked as a migration experiment.

## Startup

- `startup.md`: first file to read in a new session.

## Must Read

- `must/repo-role-and-branch-policy.md`: role of this repository and how to
  separate upstream-sync `master`, shared `l3-refactor`, and experiment
  branches.
- `must/testing-oracle-policy.md`: how to use the existing l3build tests while
  migrating behavior into `thuthesis3`.

## Overview

- `overview/project-overview.md`: repository purpose, major files, and current
  structure.

## Architecture

- `architecture/source-and-build.md`: source layout, build system, packaging,
  and test configuration.

## Guides

- `guides/refactor-branch-workflow.md`: recommended workflow for cleanup and
  LaTeX3 migration branches.

## Reference

- `reference/l3build-tests.md`: l3build test layout and useful commands.
- `reference/git-commit-conventions.md`: observed commit message style and
  recommended commit text for this fork.

## Memory

- `memory/decisions/2026-05-02-llmdoc-on-l3-refactor.md`: decision to keep
  llmdoc on `l3-refactor`.
- `memory/reflections/`: chronological reflections from future work.

Scratch investigations belong under `.llmdoc-tmp/`, not in this tree.
