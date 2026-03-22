# ichiba-evals

Centralized eval repo for [ichiba](https://github.com/nickmeehan/ichiba) plugins. Each plugin has its own eval suite under `plugins/<name>/`.

## Repo Structure

```
plugins/            # Per-plugin eval suites
  docs-kb/          # docs-kb plugin eval suite (see plugins/docs-kb/CLAUDE.md)
```

## Conventions

- Each plugin eval suite has its own `CLAUDE.md` with plugin-specific instructions
- Each plugin owns its own scoring, parsing, and runner infrastructure — no shared abstraction
- Eval configs live at `plugins/<name>/eval/eval-config.json`
- Results go in `plugins/<name>/eval/results/`
- Named baselines go in `plugins/<name>/baselines/<version>/`

## Workflow

1. Sync latest agent/skill from ichiba into `plugins/<name>/agents/`
2. Run baseline evals
3. Edit the working copy in `plugins/<name>/`
4. Re-run evals and compare against baseline
5. If improved, copy changes back to ichiba and bump versions
