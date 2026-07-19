# AGENTS.md

Operating guide for AI coding agents (and humans) working in this repository.
Read this and `context.md` before making changes. The shared method lives in
`cronologia/core` (skills: sourcing-rules, bootstrap-project, mine-video,
dossier-research); the architecture rationale in `cronologia/fsp` → `docs/adrs/`.

## What this project is

A compiled static website documenting the chronology of the **Grupo de
Puebla** — the Latin American progressive forum of individuals (2019–).
A single JSON file is the source of truth; a zero-dependency Node script
compiles it into static HTML served by GitHub Pages.

## Repository map

```
data/chronology.json     SOURCE OF TRUTH — facts, events, figures, organizations, references (hand-edited)
src/styles.css           Stylesheet (copied into the build)
scripts/validate-data.js Schema check (runs in CI before the build)
build.js                 Compiler: data/chronology.json -> docs/
test/                    node:test suites (helpers + data invariants + drift check)
.github/workflows/deploy.yml  CI: validate, test, build, drift check, Pages deploy (main + manual dispatch)
docs/                    COMPILED OUTPUT, served by GitHub Pages (committed)
```

## Working agreements

1. **Edit data, not output.** Change `data/chronology.json`, run
   `node build.js`, commit the regenerated `docs/` in the same change.
2. **Keep the build green.** `node scripts/validate-data.js`, `node --test`
   and `node build.js` must all pass; CI fails if `docs/` drifts.
3. **Cite every fact; flag every uncertainty; attribute every contested
   characterization.** The validator enforces non-empty `sources[]`.
4. **A merged PR is finished** — branch fresh from `main` for new work.

## Data quality & sourcing rules

Beyond the family's five core rules: the core service of this project is the
FSP disambiguation — the 'renamed Foro de São Paulo' narrative is opinion
journalism, presented as an attributed claim and rebutted with the
documented June 2024 Tegucigalpa coexistence; grupodepuebla.org pages are
volatile (already reorganized once) — archive on Wayback and date every
list retrieval; membership lists fluctuate — date them; most figures are
living politicians: BLP-grade care, public roles and published statements
only; critical sources (Diálogo Político, GIS Reports, Libertad Digital)
and sympathetic ones (Cubadebate, teleSUR, Lula Livre) are labeled.
