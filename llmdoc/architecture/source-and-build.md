# Source and Build Architecture

## Source Layout

The current implementation is centered on `thuthesis.dtx`, a documented LaTeX
source file. It combines user documentation and implementation sections.

The source outline includes:

- template introduction and usage documentation;
- option definitions;
- package loading;
- page layout and language setup;
- font setup;
- frontmatter/mainmatter/backmatter commands;
- title pages and copyright pages;
- abstracts, statements, lists, bibliography, appendices, resume material, and
  spine support;
- compatibility configuration for related packages.

Generated files are extracted by `thuthesis.ins`.

## Build System

`build.lua` configures l3build:

- module name: `thuthesis`;
- check engine: `xetex`;
- standard engine: `xetex`;
- test support directory: `testfiles/support`;
- test configurations: base build plus title page, cross-reference,
  nomenclature, BibTeX, and BibLaTeX configurations;
- `lvtext = ".tex"`, so test input files use `.tex`;
- `maxprintline = 79`, preserving compatibility with existing `.tlg` files.

The Makefile wraps common tasks:

- `make cls`: extract generated class/support files;
- `make doc`: build the documented source PDF;
- `make thesis`: build the example document;
- `make test`: run `l3build check`;
- `make test target=<name>`: run the repository helper for one target;
- `make save target=<name>`: update a test target through the helper script.

## Packaging

`build.lua` declares documentation, install, source, tag, and text file groups
for l3build packaging. It also enables TDS zip output and assigns explicit TDS
locations for bibliography styles and logo PDFs.

## Architectural Direction

Do not infer the final LaTeX3 module layout from this repository. This repo is
the oracle. The final module layout should be designed and maintained in
`../thuthesis3`.
