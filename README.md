# agentic-metrics-report

The published [agentic-metrics](https://github.com/grimfeld/agentic-metrics) report: one page covering every tracked repo, built from the datasets committed here.

- `datasets/<owner>/<repo>.json` (or `datasets/<alias>.json` for an anonymized repo): aggregates only, one file per tracked repo. Every number on the page traces back to these.
- `case-studies/<owner>/<repo>/<N>.md`: drafts written by `collect`. Only drafts with `approved: true` in their front matter are rendered.
- `.github/workflows/pages.yml`: renders the report with the published CLI and deploys it to GitHub Pages on every push touching `datasets/` or `case-studies/`.

## Updating a repo's numbers

Run from this repo, pointing `--checkout` at the tracked repo's local clone so its `.agentic-metrics.json` and its Claude Code transcripts are used:

```
npx agentic-metrics collect --repo grimfeld/lifeline --checkout ~/repos/lifeline
npx agentic-metrics report --out _site   # optional local preview
```

Review the new case-study drafts, set `approved: true` on the ones to publish, then commit `datasets/` and `case-studies/` and push.
