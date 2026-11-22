# ML EZ — Curriculum Roadmap (v0.2)

> Rewritten 2026-11-23. Supersedes the gamified framing in `ml-learning-app-plan.md`.
> The game layer is out; this is a **teaching tool**. If it isn't a concept made visible,
> it doesn't get built.

---

## What changed and why

The v0.1 plan was a game with a learning theme bolted on — XP, ModelDex, badges, streaks,
boss battles, localStorage saves. That's a lot of machinery that teaches nobody anything,
and it made each level cost weeks instead of hours.

**The new thesis:** machine learning is unusually hard to learn because the ideas are
*spatial* (a boundary, a spread, a curve, a cluster) but are taught *symbolically* (equations,
API calls). Show the shape first, name it second. That's the whole product.

Three rules that follow:

1. **Diagram before definition.** Every concept opens with a thing you can look at and move.
   The word and the formula come after the picture has already landed.
2. **One page, one idea, no state.** No accounts, no progress, no unlock gates, no saves.
   Someone can land on any concept from a link and get it in three minutes. Nothing to lose
   by dropping in.
3. **Data literacy is the foundation, not the intro.** You cannot teach a boundary before
   the reader can read a scatter plot. Ordering is a hard constraint, not a preference.

## Design principles

- **Every diagram is live.** A static picture of a decision boundary teaches recognition; a
  draggable one teaches the concept. Sliders over paragraphs.
- **Real numbers, small data.** 20–60 points, plotted with real axes, real ticks, real units.
  Toy data must still look like data.
- **Show the failure.** Overfitting, leakage, a bad scale, a useless feature — each is best
  taught by watching it go wrong. Failure demos are the highest-value pages in the set.
- **The "so what" line.** Every page ends with one sentence the reader could repeat to a
  friend. If that sentence doesn't exist, the page isn't finished.
- **Zero build step.** Plain HTML/CSS/JS, SVG for charts, one file per concept page.

---

## The track order

Four tracks. Each assumes the one before it. Track 0 and 1 are the actual product; 2 and 3
are the payoff.

### Track 0 — Reading Data (graphs and display)

The premise: before any model, you must be able to look at a table and see a shape.

| # | Concept | The diagram | The "so what" |
|---|---|---|---|
| 0.1 | What data *is* | A table, then the same table as points | Rows are examples, columns are measurements |
| 0.2 | Dot / scatter plots | Two columns mapped to x and y | A plot is two columns, nothing more |
| 0.3 | Histograms & distributions | Bin-width slider over a column | Shape (centre, spread, skew) is a summary |
| 0.4 | Box plots | Same column as a box + whiskers | Five numbers can describe a whole column |
| 0.5 | Relationships | Scatter + trend line, correlation slider | Correlation is direction + tightness, not cause |
| 0.6 | Overplotting & too many points | 50 points → 50,000 points | Charts lie at scale; density and alpha fix it |
| 0.7 | Bad charts | 3–4 deliberately broken charts, toggle to fixed | Axis truncation, dual axes, wrong chart type |
| 0.8 | Categories | Bar chart vs. pie, grouped bars | Comparing groups vs. showing parts of a whole |
| 0.9 | Time series | Line chart with a rolling-average toggle | Order matters when the x-axis is time |
| 0.10 | Multivariate | Scatter matrix / small multiples | You can only see 2–3 dimensions at once — hence the next track |

### Track 1 — Preparing Data (features)

Now the reader knows what a column *looks like*. This track is about making columns worth
looking at.

| # | Concept | The diagram | The "so what" |
|---|---|---|---|
| 1.1 | Feature vs. label | Table with one column pulled out as the target | Features are inputs, the label is the answer |
| 1.2 | Feature types | Numeric / ordinal / categorical / text / datetime | The type dictates every later choice |
| 1.3 | One-hot encoding | A category column exploded into 0/1 columns | Models eat numbers, not words |
| 1.4 | Missing data | Rows dropped vs. filled, and the bias each causes | Dropping is a decision, not a cleanup |
| 1.5 | Outliers | Points pulled off the cloud, mean vs. median | One value can move a whole summary |
| 1.6 | Scaling | Same data, raw axes vs. standardised | Distance-based models care about units |
| 1.7 | Distribution shaping | Log / power transform slider | Skew is fixable |
| 1.8 | Feature engineering | Combine columns: ratios, differences, date parts | New columns carry information raw ones don't |
| 1.9 | **Leakage** | A feature that "knows the answer," and the score collapsing | The most expensive mistake in the field |

### Track 2 — Choosing Features

| # | Concept | The diagram | The "so what" |
|---|---|---|---|
| 2.1 | Why fewer features help | Noise features added one by one, score falls | More columns ≠ more information |
| 2.2 | Correlation & redundancy | Correlation heatmap, near-duplicate pair | Two copies of one feature is still one feature |
| 2.3 | Filter methods | Ranked bars: variance, correlation, chi², mutual information | Score each feature alone, keep the top k |
| 2.4 | Wrapper methods | Forward selection, step by step | Try subsets, keep what improves the model |
| 2.5 | Embedded methods | L1 vs. L2 penalty, coefficients shrinking to zero | The model does the selection itself |
| 2.6 | Curse of dimensionality | Fixed points, growing dimensions, sparsity | Space gets empty fast |
| 2.7 | Dimensionality reduction | PCA on 2D data → 1D projection, explained variance | Compress many columns into a few |

### Track 3 — Models (only after the above)

The v0.1 model list, kept, but now landing on prepared features rather than raw columns.
kNN → Linear Regression → Logistic Regression → Decision Trees → Naive Bayes → SVM →
overfitting & validation → Neural Networks (intro).

**Overfitting gets promoted to a first-class level** (was missing a home in v0.1): one
complexity slider that contorts the boundary around noise while the test score falls. It
belongs right after Decision Trees, and it is probably the single most valuable page in the
whole set.

---

## Product shape

- **One page per concept.** `concepts/0.2-scatter.html`, self-contained.
- **A hub page** listing all tracks, so the whole thing is navigable from one file.
- **Each page:** title → the live diagram → 2–4 short paragraphs → the "so what" line →
  optional formula (collapsed) → prev/next links.
- **No progress tracking.** The browser remembers nothing. The URL is the only state.
- **Mobile:** diagrams must be touch-draggable, but the text can scroll. Don't build two layouts.

## What this drops from v0.1

XP, levels, badges, ModelDex, streaks, daily quests, boss challenges, localStorage save
schema, "story frame", animated cutscene hooks, unlockable deep dives. All of it. If a reader
wants a game, they'll play a game.

## Build order

1. Hub page + one fully finished concept page (0.2 scatter) as the reference template.
2. Track 0 complete — this alone is a useful, shareable artifact.
3. Track 1.3 / 1.5 / 1.6 (encoding, outliers, scaling) — the three that surprise people most.
4. Track 1.9 leakage, then Track 2.
5. Track 3.

---

## Open questions

Recorded here so they get answered rather than quietly decided. See `questions.md`.
