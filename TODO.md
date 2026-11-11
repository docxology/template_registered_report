# template_registered_report TODO

This backlog is future-only. Completed validation and dated review evidence are preserved in
the template monorepo's `docs/maintenance/exemplar-backlog-history.md` (monorepo-only path)
or in source-owned generated receipts. Each active row must retain a stable ID, size, dependency,
next action, proving artifact, acceptance command, and negative control; absence of an owner or external receipt
keeps a capability blocked rather than silently promoting it.

## Backlog operating rules

- Keep deterministic and offline defaults unchanged unless an upcoming row explicitly scopes an opt-in.
- Do not close a row until its producer, artifact, consumer, gate, and failing negative control are present.
- Treat unavailable network, LLM, container, formal-tool, and publication paths as explicit skips
  or blockers.
- Re-derive counts and receipts from live source data; never copy measurements into this planning file.

## Integrity and template-status gaps

- Keep rendered manuscript outputs and registered-report review artifacts regenerated after fixture, deviation, or sensitivity-analysis changes; preserve the fresh-regeneration contract when the artifact schema changes.

## Configurable-surface gaps

- Keep ethics-review and registered-report-stage metadata aligned with any future journal-specific fixtures.

## Documentation and signposting gaps

- Keep standalone fork guidance synchronized with the validator API.

## Test and validator gaps

- Keep rendered sensitivity-analysis tables bound to the frozen registration
  and deviation ledger.

## Minor upcoming

| ID | Status | Size | Dependency | Next action / unblock condition | Proving artifact | Acceptance command | Negative control |
| --- | --- | --- | --- | --- | --- | --- | --- |
No active rows are currently scoped at this size.

## Medium upcoming

| ID | Status | Size | Dependency | Next action / unblock condition | Proving artifact | Acceptance command | Negative control |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `REGISTERED-PUBLICATION-1` | blocked-external | Medium | Real fork and owner receipt | Obtain the required owner or external receipt to unblock; run project artifact and preflight gates and attach publication payload receipt. | publication payload receipt | `uv run pytest tests -q --no-cov` | synthetic DOI/receipt must fail |

## Major upcoming

| ID | Status | Size | Dependency | Next action / unblock condition | Proving artifact | Acceptance command | Negative control |
| --- | --- | --- | --- | --- | --- | --- | --- |
No active rows are currently scoped at this size.

## Backlog status

Rows remain active until the acceptance command and negative control pass in the same source revision.
A blocked row is a deliberate boundary, not a skipped success.

## Workflowz review — 2026-11-10

- [ ] `RR-STANDALONE-FIGURES-1` — P1 — Make the documented standalone figure-regeneration command work without the monorepo `infrastructure` package. Evidence: `scripts/generate_figures.py:25` and `scripts/generate_figures.py:27` unconditionally import `infrastructure.documentation.generated_figure_registry` via a monorepo-only path, contradicting the standalone contract in `README.md:5` and the root-level command in `README.md:63-65` / `AGENTS.md:14`; no `infrastructure/` package exists in this checkout. Observable outcome: running the documented command from the repository root renders all four PNGs plus `output/data/demo_analysis.json` and `output/figures/figure_registry.json` with no monorepo checkout present, while the monorepo invocation keeps working. Acceptance probe (from repo root): `MPLBACKEND=Agg uv run python scripts/generate_figures.py --figures-dir "$(mktemp -d)/figs" --output-figures-dir "$(mktemp -d)/outfigs" --data-dir "$(mktemp -d)/data"` exits 0 and prints the p-value summary; negative control: temporarily rename the vendored/fallback registry helper and confirm the command fails loudly rather than silently skipping the registry. Dependencies/constraints: preserve deterministic offline defaults and the existing `publish_generated_figures` provenance schema (`FIGURE_REGISTRY_SCHEMA`); prefer a small local fallback or vendored helper over adding a new dependency; do not change figure bytes. Add a script-level `main()` execution test mirroring `tests/test_generate_review_artifacts_script.py` so the argparse path is covered.
