# Decision: Keep llmdoc on l3-refactor

Date: 2026-05-02

## Context

The long-term goal is to refactor ThuThesis toward a LaTeX3-native
implementation using techniques also used in `../NJUThesis-njulug`. The sibling
`../thuthesis3` repository is the intended clean destination.

`thuthesis2e` already has a passing l3build test system and a legacy source
layout close to upstream ThuThesis. It is valuable as a regression oracle.

The repository also needs a branch that can safely hold local-only roadmap and
agent memory without making upstream synchronization harder.

## Decision

Keep upstream-sync `master` close to original ThuThesis. Add `llmdoc/` to
`l3-refactor`.

Future migration branches should merge or rebase from `l3-refactor` to inherit
the shared roadmap, branch policy, testing policy, and source/build notes.

## Consequences

Good:

- `master` remains easy to compare with and sync from upstream ThuThesis;
- future agents can start from the same roadmap on `l3-refactor`;
- architectural branches have clear merge rules;
- test additions and behavior-preserving cleanup have a documented local base;
- the distinction between `thuthesis2e` and `thuthesis3` is explicit.

Tradeoff:

- migration branches must remember to sync from `l3-refactor`, not directly
  from `master`, when they need local project memory.

The tradeoff is acceptable because it preserves a clean upstream-sync branch
while still giving the long-running migration a stable local base.
