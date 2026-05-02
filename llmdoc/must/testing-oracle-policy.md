# Testing Oracle Policy

## Purpose

The l3build suite in `thuthesis2e` is the main reason to keep this repository
stable. It provides a regression oracle for behavior that `../thuthesis3`
should eventually reproduce or intentionally replace.

## Rules

Keep tests close to `l3-refactor`:

- test additions and fixture corrections usually belong on `l3-refactor`;
- if an architectural branch discovers a missing regression case, add that test
  to `l3-refactor` first when possible;
- architectural branches should then merge or rebase from `l3-refactor`.

Treat passing tests as necessary but not sufficient:

- `.tlg` equality proves log-level compatibility for covered scenarios;
- it does not prove PDF visual identity, typography, or semantic API quality;
- cover-page, frontmatter, and bibliography changes may need focused visual or
  PDF-level checks in addition to l3build.

Use targeted verification during agent work:

- after each code change, run only the l3build target or configuration relevant
  to the touched behavior;
- do not run the complete `l3build check` suite by default, because it is
  intentionally thorough and expensive;
- let the human maintainer run the complete suite unless they explicitly ask the
  agent to run it;
- when the human reports full-suite failures, treat those as follow-up targets
  and debug the reported cases directly.

Port tests forward:

- once a behavior area is implemented in `../thuthesis3`, copy or adapt the
  relevant l3build tests there;
- keep test names close enough that failures can be traced back to
  `thuthesis2e`;
- when behavior intentionally changes, document the reason in `thuthesis3`.

## Branch Interpretation

On a cleanup branch, a failing test usually means the cleanup changed behavior
and should be fixed before merge.

On a LaTeX3 experiment branch, a failing test may be useful evidence. Either
fix the branch to preserve behavior or record that the behavior should differ
in `../thuthesis3`.
