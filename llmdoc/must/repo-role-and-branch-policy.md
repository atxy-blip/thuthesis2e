# Repository Role and Branch Policy

## Decision

Keep upstream-sync `master` close to original ThuThesis. Keep `llmdoc/` and
shared migration policy on `l3-refactor`.

This documentation is not part of a single refactor experiment. It describes
the role of the repository, the branch policy, and the test oracle. Future
branches such as `refactor/xtemplate-cover` and `refactor/l3keys-options`
should merge or rebase from `l3-refactor` to inherit it.

## Mental Model

`thuthesis2e/master` is the upstream-sync reference:

- close to original ThuThesis;
- useful for comparison and upstream synchronization;
- not the place for local-only migration memory.

`thuthesis2e/l3-refactor` is the shared local development base:

- inherits from upstream-sync `master`;
- carries llmdoc and roadmap decisions;
- keeps the l3build oracle available for migration work;
- may receive tests, documentation, and behavior-preserving cleanup that support
  the long-running LaTeX3 migration.

`thuthesis2e/refactor/*` branches are experiments:

- each branch should test one migration idea or one cleanup theme;
- each branch should usually start from or sync with `l3-refactor`;
- architectural branches may temporarily diverge from legacy internals;
- successful LaTeX3-native ideas are copied or adapted into `../thuthesis3`.

`../thuthesis3` is the destination:

- clean top-level repository layout;
- LaTeX3-native source structure;
- public contribution surface for the long-running rewrite.

## Merge Rules

Commit to `l3-refactor` when the change is local migration infrastructure,
project memory, tests, or cleanup that should be shared by future experiment
branches.

Good candidates for `l3-refactor`:

- adding or improving tests;
- fixing test fixtures;
- documenting repo policy;
- removing duplicated legacy code without changing behavior;
- small compatibility fixes that preserve intended original behavior.

Poor candidates for upstream-sync `master`:

- llmdoc and local roadmap notes;
- replacing the option system with a new `l3keys` architecture;
- replacing cover construction with an `xtemplate` architecture;
- introducing hook-based document phases as the primary execution model;
- reorganizing the repository to match the final `thuthesis3` layout;
- any change whose main purpose is the new LaTeX3 ontology.

## Top-Level Structure Policy

Do not aggressively simplify upstream-sync `master` just for aesthetics. Its
layout is part of the current oracle: source files, release files, support
files, and tests are easy to compare with upstream ThuThesis.

If `thuthesis2e` needs local project memory or branch-management files, keep
them on `l3-refactor`.

Do simplify the top level in `../thuthesis3`, where the new architecture and
new contribution history live.

## Contribution Visibility

For long-running public work, commit primary LaTeX3 implementation progress in
`../thuthesis3`. Use `thuthesis2e/l3-refactor` and child branches to validate
behavior against the old suite, then port the result.
