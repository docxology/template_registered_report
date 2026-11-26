# Documentation maintenance

Use [README.md](README.md) as the documentation entry point. Keep the
supported standalone and shared-runner commands in [rendering.md](rendering.md).

The canonical source is [manuscript/](manuscript/README.md). Keep the numbered
sections in order and configuration in [config.yaml](manuscript/config.yaml).
Treat `{{TOKEN}}` placeholders as render-time variables.

Keep confirmatory claims tied to the frozen
[registration](../data/example_registration.json) and
[hypothesis ledger](manuscript/02_hypotheses.md). Tie exploratory claims to the
[deviation ledger](manuscript/05_deviations.md). Derive values and figure
captions from the generated evidence.

Follow root [AGENTS.md](../AGENTS.md) for the repository's evidence and
verification conventions.
