# Startup

Read this file first when starting work in `thuthesis2e`.

## Repository Role

`thuthesis2e` is a forked, original-compatible ThuThesis codebase. Its main
value is that it already has a broad l3build regression test suite and a
known-working legacy implementation.

Use it as:

- a stable behavior oracle for the original 2e implementation;
- a place for behavior-preserving cleanup that makes the oracle easier to read;
- a laboratory for proving one migration idea at a time against old behavior.

Do not use it as the final destination for the LaTeX3-native architecture.
That destination is the sibling `../thuthesis3` repository.

## Required Reading

Before non-trivial edits, read:

1. `llmdoc/must/repo-role-and-branch-policy.md`
2. `llmdoc/must/testing-oracle-policy.md`
3. `llmdoc/architecture/source-and-build.md`
4. the relevant guide or reference file for the task

## Default Working Rule

Classify the branch before editing:

- Upstream sync: keep `master` close to upstream ThuThesis and avoid committing
  local migration memory there.
- Shared local development: use `l3-refactor` for llmdoc, roadmap, test policy,
  and behavior-preserving cleanup that supports the migration.
- Behavior-preserving cleanup: may later be proposed back toward `master` or
  upstream if tests still pass and the result remains conceptually legacy
  `thuthesis`.
- LaTeX3 architecture experiment: prove equivalence here if useful, then
  copy/adapt the design into `../thuthesis3`; do not merge the architectural
  rewrite into upstream-sync `master`.
- Test or fixture improvement: usually belongs on `l3-refactor` first, because
  it improves the local oracle used by migration branches.

## Current Important Branch Pattern

`refactor/xtemplate-cover` is a migration experiment branch. It may use the
existing l3build tests to prove cover-page equivalence, but the successful
design should be adapted into `../thuthesis3`.

## Documentation Rule

Stable project memory belongs in `llmdoc/` on `l3-refactor`. Temporary notes
and investigations belong in `.llmdoc-tmp/`.
