# figures - template_registered_report

Committed manuscript figures for the registered-report exemplar. Each PNG is
regenerated deterministically by `scripts/generate_figures.py` from tested
functions in `src/registered_report/` — the figure-data helpers in
`demo_study.py` and the renderers in `figures.py`:

- `hypothesis_map.png` — registered hypothesis-to-outcome-to-analysis mapping
  (`fig:hypothesis_map`).
- `analysis_dag.png` — registered-report workflow with the pre-results lock
  boundary (`fig:analysis_dag`).
- `deviation_timeline.png` — preregistration-versus-executed deviation ledger
  timeline (`fig:deviation_timeline`).
- `permutation_result.png` — seeded permutation null distribution and observed
  difference for the demonstration study (`fig:permutation_result`).

Follow the [evidence generation guide](../../rendering.md#regenerate-the-evidence)
to regenerate the figures after changing the registration fixture or the
rendering functions.
