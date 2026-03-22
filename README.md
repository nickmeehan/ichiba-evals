# ichiba-evals

Centralized eval repo for [ichiba](https://github.com/nickmeehan/ichiba) plugins.

## Plugin Eval Suites

- **[docs-kb](plugins/docs-kb/)** — Evaluates the `doc-traversal` agent against a 188-doc synthetic corpus (6 test queries, 60 trials)

## Quick Start

```bash
# Score existing results
python3 plugins/docs-kb/eval/score-results.py plugins/docs-kb/eval/results/

# Compare against baseline
python3 plugins/docs-kb/eval/score-results.py plugins/docs-kb/baselines/v1.0.2/
```

See [plugins/docs-kb/CLAUDE.md](plugins/docs-kb/CLAUDE.md) for full eval workflow.
