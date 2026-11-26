# Generate evidence and render the manuscript

## Regenerate the evidence

From the standalone project root, run:

```sh
uv sync --locked --extra dev
MPLBACKEND=Agg uv run --no-sync python scripts/generate_figures.py
uv run --no-sync python scripts/generate_review_artifacts.py
```

The figure script executes the seeded permutation analysis, writes
`output/data/demo_analysis.json`, and generates four PNGs in
`docs/manuscript/figures/`. It mirrors those PNGs into `output/figures/`
and writes `figure_registry.json` after all declared figures are available.
The review script creates the frozen registration, review packet, deviation
ledger, sensitivity findings, and adherence report in `output/reports/`.

## Set up the pinned renderer

The manuscript uses the
[docxology/template](https://github.com/docxology/template/tree/87704feae0a4490ef7dad9c931d268e8c30273c2)
renderer. Install Git, uv, Pandoc, and XeLaTeX with the TeX Live packages listed
in the [renderer guide](https://github.com/docxology/template/blob/87704feae0a4490ef7dad9c931d268e8c30273c2/docs/RUN_GUIDE.md).
Install a version of
[pandoc-crossref](https://github.com/lierdakil/pandoc-crossref/releases/tag/v0.3.17.0c)
that matches Pandoc. The linked release matches Pandoc 3.1.11.1.

From the standalone checkout's root, run:

```sh
registered_report_checkout="$PWD"
git clone https://github.com/docxology/template.git ../registered-report-renderer
cd ../registered-report-renderer
git checkout --detach 87704feae0a4490ef7dad9c931d268e8c30273c2
uv sync --locked --no-dev
mkdir -p projects/working
ln -s "$registered_report_checkout" "projects/working/$(basename "$registered_report_checkout")"
registered_report_project="working/$(basename "$registered_report_checkout")"

uv run --no-sync python scripts/pipeline/stage_03_render.py --project "$registered_report_project"
uv run --no-sync python scripts/pipeline/stage_04_validate.py --project "$registered_report_project"
```

The renderer resolves the numbered Markdown, `config.yaml`, preamble,
bibliography, and figures under `docs/manuscript/`. If the project already
lives inside the renderer checkout, pass its existing project selector to both
stages instead of creating the link. Run Stage 04 with the manuscript sources
in Git's index so the provenance report can include them.

The stages write the combined PDF to `output/pdf/`, combined HTML to
`output/web/index.html`, slide PDFs to `output/slides/`, and validation and
provenance reports to `output/reports/` in the standalone project. Check the
combined editions for the ordered sections, formatted bibliography, and four
figures. The committed `output/` snapshot can change during regeneration.
