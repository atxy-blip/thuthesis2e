# l3build Tests

## Layout

Tests live under `testfiles/`.

Representative groups:

- `01-title-page/`: Chinese title-page cases.
- `01-title-page-en/`: English title-page cases.
- `10-bibtex/`: BibTeX bibliography cases.
- `10-biblatex/`: BibLaTeX bibliography cases.
- `08-notation-nomencl/`: nomenclature-related cases.
- top-level `*.tex` and `*.tlg`: frontmatter, contents, figures, tables,
  appendices, statements, resume, and package compatibility cases.

Support files:

- `testfiles/support/*.bib`: bibliography fixtures.
- `testfiles/support/thuthesis-log-test-config.tex`: shared test config.
- `testfiles/config-*.lua`: l3build check configurations.

## Useful Commands

Run a focused target after a narrow change:

```sh
l3build check <target>
```

Run a focused configuration for a covered area:

```sh
l3build check --config testfiles/config-title-page
```

Run all configured tests only when explicitly requested or when preparing a
final integration point:

```sh
l3build check
```

Via Makefile:

```sh
make test
```

Run one helper target:

```sh
make test target=<target>
```

Update one helper target:

```sh
make save target=<target>
```

## Notes

`build.lua` excludes some broad test patterns from the default check:

- `06-*`
- `07-*`
- `09-*`
- `*-hyperref`

Check whether an excluded case matters before relying on default test success
for a refactor.

Current workflow preference: agents should run relevant focused checks after
changes, while the human maintainer runs the complete suite and reports any
remaining failures such as package compatibility regressions.
