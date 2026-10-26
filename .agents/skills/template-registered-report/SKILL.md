---
name: template-registered-report
description: Registered-report exemplar for preregistration locking, deviation ledgers, replication, and confirmatory claim boundaries.
version: 0.1.0
author: docxology
license: MIT
tags: [exemplar, preregistration, replication, registered-report]
---

# template-registered-report

Load this skill when working inside this repository (standalone mirror of
`projects/templates/template_registered_report/`).

## When to Use

- Creating or reviewing a preregistered study.
- Auditing deviations between a frozen plan and executed analyses.
- Forking a registered-report scaffold.

## Quick Reference

```bash
uv sync --extra dev
uv run pytest tests --cov=src --cov-fail-under=90
```

Inside the template monorepo, from the monorepo root:
`uv run python scripts/pipeline/stage_01_test.py --project templates/template_registered_report --project-only`.

## Pitfalls

- Do not backfill hypotheses from observed results.
- Label exploratory analyses explicitly.
- Regenerate figures through `scripts/generate_figures.py`; it writes
  `output/figures/figure_registry.json` only after all four registered-report
  figures exist, and supports explicit temp destinations for isolated checks.
- Regenerate review artifacts with `scripts/generate_review_artifacts.py`; the
  suite binds the committed `output/reports/*.json` artifacts and the
  manuscript's sensitivity row and deviation ledger to a fresh regeneration, so
  never hand-edit those files or the bound prose.
