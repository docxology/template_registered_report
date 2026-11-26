# Registered report documentation

This exemplar demonstrates how to freeze a registered protocol, record
deviations, and distinguish confirmatory findings from exploratory results.
The included data and results come from a seeded demonstration.

- [Standalone fork guide](standalone.md)
- [Evidence generation and manuscript rendering](rendering.md)
- [Manuscript and section map](manuscript/README.md)
- [Registration and claims fixtures](reference/data.md)
- [Generation scripts](reference/scripts.md)
- [Python implementation](reference/implementation.md)
- [Test coverage](reference/tests.md)
- [Maintenance backlog](backlog.md)

## Setup and tests

Install [uv](https://docs.astral.sh/uv/getting-started/installation/) and run
these commands from the repository root. The project selects Python 3.14 via
`.python-version`.

```sh
uv sync --locked --extra dev
uv run --no-sync pytest tests --cov=src --cov-fail-under=90
```

## Configuration and artifacts

| Path | Role |
| --- | --- |
| [docs/manuscript/config.yaml](manuscript/config.yaml) | Render settings, authorship, and publication metadata |
| [docs/manuscript/config.yaml.example](manuscript/config.yaml.example) | Starting metadata for forks |
| [data/example_registration.json](../data/example_registration.json) | Preregistered hypotheses, outcomes, and analysis plan |
| [data/claim_ledger.yaml](../data/claim_ledger.yaml) | Claim-to-evidence mapping |
| [domain_profile.yaml](../domain_profile.yaml) and [experiment_plan.yaml](../experiment_plan.yaml) | Template domain and experiment settings |
| [output/](../output/) | Committed reproducibility snapshot with generated evidence and rendered artifacts |

The validator freezes plans with a deterministic hash, checks required sections,
and compares executed analyses with registered outcomes. Registration schema v2
migrates the earlier fixture without inventing missing values. The review packet
records ethics and stage metadata, sensitivity checks, confirmatory and
exploratory outcomes, and the receipt requirements for owner-gated publication.
