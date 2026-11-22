# machineLearningEZ

A quick tool for teaching machine learning — concepts first, made visible as live diagrams.

No accounts, no progress saving, no game layer. One page per concept, each one a live,
draggable diagram that shows a single idea.

## The plan

| File | What it is |
|---|---|
| [ml-learning-app-plan.md](ml-learning-app-plan.md) | **Curriculum roadmap (v0.2)** — the rewrite. Read this first. |
| [track-0-reading-data.md](track-0-reading-data.md) | Track 0 — graphs and displaying data (10 pages) |
| [track-1-features.md](track-1-features.md) | Track 1 — feature engineering and preparation (9 pages) |
| [track-2-feature-selection.md](track-2-feature-selection.md) | Track 2 — feature selection and dimensionality (7 pages) |
| [page-template.md](page-template.md) | The spec every concept page follows |
| [questions.md](questions.md) | Open decisions — answer inline |

## Order

1. **Track 0 — Reading data.** Before any model, you must be able to look at a table and see
   a shape. Scatter plots, histograms, box plots, correlation, bad charts, too many points,
   too many columns.
2. **Track 1 — Preparing data.** Column types, one-hot encoding, missing data, outliers,
   scaling, transforms, feature engineering, leakage.
3. **Track 2 — Choosing features.** Redundancy, filters, wrappers, lasso/ridge, the curse of
   dimensionality, PCA.
4. **Track 3 — Models.** kNN, regression, trees, overfitting, and the rest — only once the
   reader can read and prepare data.

## What changed from v0.1

The original draft was a game: XP, badges, a ModelDex, streaks, boss battles, localStorage
saves. All of that is dropped. This is a teaching tool — if a page isn't a concept made
visible, it doesn't get built.

## Status

Planning. Nothing built yet. Next step: the reference page, `0.2 Scatter plots`, as the
template everything else follows.
