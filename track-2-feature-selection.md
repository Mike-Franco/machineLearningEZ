# Track 2 — Choosing Features

Track 1 made every column usable. Track 2 asks a different question: *do you need this column
at all?* Fewer, better features beat more, worse ones — and the reasons are geometric, which
means they can be drawn.

Short track, seven pages. It lands after Track 1 because selection methods are meaningless on
badly encoded columns.

---

## 2.1 — Why fewer features help

**Diagram:** a starting set of 4 informative features. A button adds a noise feature; each
addition redraws a model's decision boundary and a score bar.

**Interaction:** add / remove noise features one at a time.

**Text:** every column is a chance for the model to find a coincidence and believe it. With
enough irrelevant columns, a flexible model will always find something that fits the training
data and means nothing. This is the same disease as overfitting, caught earlier.

**So what:** *More columns give the model more chances to be confidently wrong.*

---

## 2.2 — Redundancy and correlation

**Diagram:** a correlation heatmap over 6 columns, with one near-duplicate pair highlighted.
Clicking a cell shows the two columns' scatter plot.

**Interaction:** click cells; a "duplicate this column" button that adds an exact copy and
shows the heatmap go to 1.0.

**Text:** two columns that carry the same information are one column wearing a hat. They split
the importance between them, make interpretation unreliable, and make linear models unstable.
Correlation finds the obvious duplicates; it misses nonlinear redundancy.

**So what:** *Two copies of a feature is still one feature — and it makes the model lie about
what matters.*

---

## 2.3 — Filter methods

**Diagram:** a bar chart ranking all features by a score, with a "keep top k" cutoff line.
A toggle switches the scoring method: variance, correlation with the label, chi², mutual
information.

**Interaction:** method toggle; k slider.

**Text:** filters score each column on its own, without a model. Fast, and they miss
interactions entirely. Variance throws away constants. Correlation only sees straight lines.
Mutual information catches curves that correlation can't — but needs more data to be reliable.

**So what:** *A filter scores each column alone — cheap, fast, and blind to teamwork.*

**Deliberate failure:** a feature that is useless alone but essential in combination. Filters
drop it. The page shows what was lost.

---

## 2.4 — Wrapper methods

**Diagram:** a grid of all 2^5 feature subsets with a step-by-step forward-selection path
highlighted as the score rises, then dips.

**Interaction:** step through forward selection; a second toggle for backward elimination.

**Text:** wrappers actually train a model on each subset and keep what scores best. They find
interactions filters can't see. They also cost one model per candidate and overfit the
validation set if you're careless about how many times you peek.

**So what:** *Wrappers ask the model which columns it likes — and pay for the answer in compute.*

---

## 2.5 — Embedded methods

**Diagram:** a coefficient bar chart for a linear model, with an L1/L2 toggle and a penalty
slider. Under L1, coefficients visibly snap to exactly zero as the penalty grows.

**Interaction:** penalty strength slider; L1 vs L2 toggle.

**Text:** embedded methods select while they fit. L1 (lasso) pushes coefficients to zero —
it performs selection. L2 (ridge) shrinks them smoothly but keeps them all. This is why lasso
is the default when you suspect most features are noise.

**So what:** *Lasso deletes features by making their weights exactly zero.*

**Deliberate failure:** crank the penalty on L2 and watch the coefficients shrink toward zero
without ever reaching it — so nothing is actually selected.

---

## 2.6 — The curse of dimensionality

**Diagram:** a unit cube in 2D, 3D, then n dimensions, with a readout of the average distance
between random points and the fraction of the volume near the edge.

**Interaction:** dimension slider from 1 to 50; points visibly spread into emptiness.

**Text:** as dimensions grow, points get further apart, distances stop being meaningful, and
you need exponentially more data to fill the space. This is why "just add more features" fails,
and why distance-based models (kNN, k-means) struggle in high dimensions.

**So what:** *In high dimensions everything is far from everything else, and "near" stops
meaning anything.*

---

## 2.7 — Dimensionality reduction

**Diagram:** 2D data with correlated features, and its projection onto the first principal
component. A second panel shows explained-variance bars.

**Interaction:** rotate the projection axis by hand to find the best direction, then compare
with PCA's answer; slider for number of components kept.

**Text:** PCA finds the directions in which the data varies most and rewrites the columns as
those directions. You trade interpretability for compactness: the new columns are combinations,
so you can no longer say what one of them means. Explained variance tells you how much you lost.

**So what:** *PCA keeps the spread and throws away the names.*

---

## Track 2 exit test

1. You have 200 columns and 300 rows. What do you do first, and why?
2. Name one thing a filter method can't see that a wrapper can.
3. What's the difference in outcome between lasso and ridge on a set of mostly-noise features?
4. Why does kNN get worse as you add dimensions, even if the extra dimensions are informative?
5. You reduce 50 columns to 3 with PCA. What did you gain, and what did you lose?
