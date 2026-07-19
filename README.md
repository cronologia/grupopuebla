# Grupo de Puebla — Cronologia

A compiled static website documenting the chronology of the **Grupo de
Puebla** (founded Puebla, Mexico, July 2019): the encuentros, declarations
and CLAJUD — and the disambiguation from the
[Foro de São Paulo](https://github.com/cronologia/fsp), with which it is
constantly conflated (distinct organizations: 1990 vs 2019, parties vs
individuals, coexisting to this day).

Part of the [Cronologia](https://cronologia.github.io) family; built from the
[`core`](https://github.com/cronologia/core) template. Single JSON source of
truth (`data/chronology.json`), zero-dependency build, GitHub Pages.

```bash
node scripts/validate-data.js && node --test && node build.js
```

Publish: Settings → Pages → GitHub Actions + Actions variable
`ENABLE_PAGES=true` (with `main` as default).
