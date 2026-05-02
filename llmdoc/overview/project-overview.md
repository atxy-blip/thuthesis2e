# Project Overview

`thuthesis2e` is a fork of ThuThesis, the Tsinghua University thesis LaTeX
template. This repository currently keeps the legacy documented-source layout
and a broad l3build regression suite.

## Main Files

- `thuthesis.dtx`: documented source and implementation.
- `thuthesis.ins`: extraction script for generated class/style files.
- `build.lua`: l3build configuration.
- `Makefile`: convenience targets for class generation, documentation, example
  compilation, release checks, and tests.
- `thusetup.tex`: example setup data.
- `thuthesis-example.tex`: example thesis document.
- `*.bbx`, `*.cbx`, `*.bst`: bibliography styles.
- `thu-fig-logo.pdf`, `thu-text-logo.pdf`: bundled Tsinghua visual assets used
  by the template.

## Main Directories

- `testfiles/`: l3build regression tests and expected `.tlg` logs.
- `testfiles/support/`: bibliography and support files for tests.
- `testfiles/support-pdf/`: PDF support fixtures.
- `data/`, `figures/`, `ref/`: example document assets.
- `utils/`: release and build helper scripts.
- `llmdoc/`: stable project memory for agent-assisted development.

## Sibling Repositories

- `../thuthesis3`: target LaTeX3-native implementation and clean repository
  structure.
- `../NJUThesis-njulug`: reference for the desired modernized structure and
  development style.

## Development Posture

Prefer narrow, test-backed changes in this repository. Broad redesign belongs
in `../thuthesis3` after being validated here when useful.
