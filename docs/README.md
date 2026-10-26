# docs/ — template_registered_report

Human entry point for this repository's documentation. The repo's own README.md
remains the primary overview; this directory collects stable how-to and
reference material.

## What this repo is

`template_registered_report` — a public exemplar for registered reports,
preregistration, replication, and robustness-audit workflows. It makes the
planned analysis, frozen hypothesis ledger, deviations, and post-run claims
auditable.

## Repository layout (top level)

| Path | Role |
|---|---|
| `src/` | Project business logic |
| `scripts/` | Thin orchestrators importing from `src/` |
| `tests/` | Project test suite |
| `manuscript/` | Registered-report sections (abstract → deviations → references), `config.yaml`, figures |
| `output/` | Reproducibility bundle (tracked, like every other public exemplar) |
| `data/` | Project data incl. `claim_ledger.yaml`, `example_registration.json` |
| `docs/` | This documentation directory |

## Running

From this repository root (per root `README.md`):

```bash
uv sync --extra dev
uv run pytest tests
```

Inside the template monorepo the same project runs from the monorepo root with
`uv run python scripts/pipeline/stage_01_test.py --project templates/template_registered_report --project-only`.

Forks: copy `manuscript/config.yaml.example` to `manuscript/config.yaml`.

## Testing

Project pytest config lives in `pyproject.toml` (`testpaths = ["tests"]`,
`pythonpath = [".", "src"]`). From this repository root:

```bash
uv run pytest tests --cov=src --cov-fail-under=90
```

## Documentation maintenance

Docs here are hand-maintained, short, and evidence-based: every factual claim
traces to a repo file (README, AGENTS.md, config, source headers). Cross
references to monorepo-level guides (`docs/`, `infrastructure/` at the template
root) resolve only inside a full template checkout, not in this standalone
checkout.
