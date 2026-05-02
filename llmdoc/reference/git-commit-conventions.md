# Git Commit Conventions

This repository follows the upstream ThuThesis history more than a strict
machine-enforced convention.

## Evidence From History

Recent non-merge commits commonly use short imperative subjects:

- `Fix option conflict with nomencl`
- `Update test files`
- `Add Schwarzman Scholars style`
- `Remove spine from doc and configs`
- `Change \statement to include header by default`
- `Bump TeX-Live/setup-texlive-action from 3 to 4 (#1052)`

Some commits use lightweight lowercase scopes:

- `doc: update CHANGELOG, add more instructions on \statement in example`
- `tests: update according to latest TeX Live`
- `ci: bump actions`
- `feat: disable multiple invocation of some commands (#1041)`

Merge commits usually keep GitHub's default form:

- `Merge pull request #1056 from tuna/statement`

## Subject Style

Prefer one-line imperative subjects:

- start with a verb such as `Add`, `Fix`, `Update`, `Remove`, `Change`,
  `Deprecate`, `Rename`, `Use`, or `Bump`;
- keep the subject specific and compact;
- use present-tense imperative phrasing, not past tense;
- capitalize sentence-style subjects unless using an existing lowercase scope.

Good examples for this fork:

- `Add llmdoc project memory`
- `Document refactor branch policy`
- `Update title page test fixtures`
- `Fix spacing around \eqref with mathtools`

## Scopes

Scopes are optional. Use them when they match existing history and clarify the
area:

- `doc:` for user-facing documentation, changelog, or README updates;
- `tests:` for test fixture changes;
- `ci:` for GitHub Actions or automation;
- `feat:` sparingly, mostly for user-visible template features.

Do not force Conventional Commits for every change. A plain imperative subject
is more consistent with most of the project history.

## Issue and PR References

Append issue or PR references when directly relevant:

- `Fix delimiter of two consecutive citation numbers (fix #1027)`
- `Use discipline as subject in PDF document properties (resolve #1025)`
- `Change the comma in author-year citation to halfwidth (#1054)`

For internal fork maintenance with no upstream issue, omit the reference.

## Body Style

Most small commits do not need a body. Add a body when the reason is not obvious
from the diff, especially for:

- repository policy decisions;
- test oracle changes;
- compatibility tradeoffs;
- LaTeX3 migration experiments whose result will be ported to `../thuthesis3`.

Use a concise body that explains why the change exists and what policy it
establishes.

## Recommended Commit for Adding llmdoc

Use this subject:

```text
Add llmdoc project memory
```

Suggested body:

```text
Document the role of thuthesis2e as the stable 2e regression oracle for the
LaTeX3 rewrite.

Record the branch policy, l3build testing policy, source/build overview, and
refactor workflow so future migration branches can inherit the same guidance
from l3-refactor.
```
