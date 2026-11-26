# scripts - template_registered_report

Thin orchestrators. All computation is imported from `src/registered_report/`;
these scripts only handle seeded layout and file I/O. Use the [rendering guide](../rendering.md) for the shared pipeline.

`generate_figures.py` executes the registered analysis on deterministic
demonstration data. From the [configured standalone checkout](../README.md#setup-and-tests), it renders the four manuscript figures into
`docs/manuscript/figures/`, writing the executed analysis to
`output/data/demo_analysis.json`:

```bash
MPLBACKEND=Agg uv run --no-sync python scripts/generate_figures.py
```

`generate_review_artifacts.py` creates deterministic registered-report review
artifacts from `data/example_registration.json`: frozen registration, review
packet, deviation ledger, sensitivity findings, and adherence report.

```bash
uv run --no-sync python scripts/generate_review_artifacts.py
```
