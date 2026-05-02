# l3keys Compatibility Rule

This branch migrates legacy key handling in small, behavior-preserving slices.

## Public Interface

Keep the existing public setup syntax unless a later branch explicitly changes
the API:

```tex
\thusetup{
  title  = {...},
  author = {...},
}
```

Do not add a grouped public API such as `\thusetup[info]{...}` in this
repository slice. `njuthesis` uses grouped modules, but `thuthesis2e` is the
legacy behavior oracle and should prioritize backward compatibility over a
cleaner grouping model.

Do not normalize paragraph tokens in `\thusetup` input to make blank-line
separated key lists work. Legacy LaTeX key-value usage treats paragraph tokens
inside setup arguments as invalid, and silently removing `\par` tokens risks
changing user-provided values.

Define user-facing commands with `\NewDocumentCommand` from `xparse` instead of
legacy `\newcommand` when the surrounding code is already using LaTeX3
interfaces. This keeps public command construction aligned with the LaTeX3
migration direction while preserving the old argument shape.

## Internal Compatibility

When replacing the key parser with `l3keys`, preserve the legacy internal macro
surface used by the rest of `thuthesis.dtx`:

- values remain available as macros such as `\thu@title`, `\thu@author`, and
  `\thu@degree@category`;
- choice keys continue to set existing booleans such as
  `\ifthu@degree@doctor`;
- existing `\thu@option@hook{<key>}{...}` callbacks still run after a key is
  set;
- class options keep working until the class-option layer is migrated in a
  separate step.

## Migration Order

Prefer this order for `refactor/l3keys-info`:

1. Move `\thusetup` parsing to `l3keys` while preserving old key names and old
   internal macros.
2. Prove title-page and setup behavior with l3build.
3. Migrate class-option processing away from `kvoptions` separately.
4. Only consider grouped modules in `../thuthesis3`, or in a clearly marked API
   change branch.
