# Reflection: Git Commit Conventions

Date: 2026-05-02

## Trigger

The user asked to summarize commit conventions and document them before drafting
the commit that adds `llmdoc/`.

## Observation

The repository does not consistently use strict Conventional Commits. Most
recent subjects are imperative, sentence-style summaries such as `Fix ...`,
`Update ...`, `Add ...`, `Remove ...`, and `Change ...`. Lightweight scopes
such as `doc:`, `tests:`, `ci:`, and occasional `feat:` also appear.

## Lesson

For this fork, match upstream style unless there is a concrete reason to impose
a stricter format. The best default is a compact imperative subject, with an
optional body for repository policy or migration context.

## Promotion

The stable guidance was promoted to
`llmdoc/reference/git-commit-conventions.md`.
