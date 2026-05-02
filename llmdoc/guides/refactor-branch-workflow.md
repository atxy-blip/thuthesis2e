# Refactor Branch Workflow

Use this workflow before starting a `thuthesis2e/refactor/*` branch.

## 1. Classify the Branch

Choose one category:

- cleanup branch: behavior-preserving improvement of the legacy codebase;
- test branch: adds or repairs oracle coverage;
- migration experiment: tests a LaTeX3-native idea against old behavior.

Write the category in the branch notes or opening commit message.

## 2. Start From `l3-refactor`

Use current `l3-refactor` for shared documentation and test policy. If already
on a long-running branch, regularly merge or rebase from `l3-refactor` to
inherit new tests and llmdoc updates.

## 3. Keep Experiments Narrow

A migration branch should prove one idea:

- `refactor/xtemplate-cover`: cover construction only;
- `refactor/l3keys-options`: option system only;
- `refactor/hook-frontmatter`: frontmatter phase model only.

Avoid combining source movement, formatting churn, API redesign, and behavior
changes in one branch.

## 4. Preserve or Explain Behavior

For cleanup branches, all relevant l3build tests should pass before merge.

For migration experiments, failing tests should be resolved or explained before
the idea is ported into `../thuthesis3`.

## 5. Port, Then Decide

After an experiment succeeds:

1. adapt the design into `../thuthesis3`;
2. port relevant tests into `../thuthesis3`;
3. decide whether anything from the branch is a behavior-preserving improvement
   that should be kept on `l3-refactor` or proposed upstream separately;
4. leave architectural-only code out of upstream-sync `master`.
