# docs/AGENTS.md — template_registered_report

Agent-facing notes for this repository's `docs/` directory.

## Layout

- `README.md` — human entry point: what the repo is, directory map, run/test
  commands (copied from root `README.md` and `pyproject.toml`).
- This file — agent conventions for maintaining `docs/`.

## Key structure (from root README / manuscript)

- `manuscript/02_hypotheses.md` — frozen hypothesis ledger.
- `manuscript/05_deviations.md` — deviation ledger between plan and execution.
- Confirmatory-versus-exploratory claim boundaries are locked before results
  are interpreted (root `README.md`, "When to use this template").
- `data/claim_ledger.yaml` and `data/example_registration.json` carry the
  registration/claims data.

## Conventions observed in this repo

- Manuscript follows the shared template standard: `manuscript/config.yaml` is
  the live metadata source; `config.yaml.example` is the fork template.
- `{{TOKEN}}` placeholders in manuscript markdown are render-time variables,
  not defects; they resolve via the manuscript-variables pipeline.
- Decision memory: root `README.md` links the monorepo
  `docs/rules/memory_and_decision_records.md` guidance (resolves inside a full
  template checkout only).
- Docs changes should be committed path-scoped to `docs` (and `manuscript`
  when applicable), never mixed with code changes.

## Scope rules for agents

- DOCS + MANUSCRIPT CONTENT ONLY: do not modify `src/`, `tests/`, `scripts/`,
  or build configs when working in `docs/`.
- Never fabricate numbers: measured counts belong to generated docs at the
  monorepo level (`docs/_generated/COUNTS.md`), not hand-written prose here.
