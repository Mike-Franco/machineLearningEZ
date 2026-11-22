# Track 1 — Preparing Data (Features)

The bridge from "I can read a chart" to "I can build a model." Every page here is about a
column: what type it is, whether it's trustworthy, whether it's on the right scale, and
whether it should exist at all.

These pages carry most of the "aha" moments in the whole tool, because feature mistakes are
where beginners lose weeks and never find out why.

---

## 1.1 — Features and the label

**Diagram:** one table with a column pulled out and set above the rest, labelled *label*,
with the remaining columns labelled *features*.

**Interaction:** pick which column is the label; the page re-draws the split and shows what
the model would be asked to predict.

**Text:** the label is the thing you want to know; the features are the things you're allowed
to know. Changing which is which changes the whole problem — and some choices make it
impossible (predicting a value from itself).

**So what:** *Features are what you know at prediction time; the label is what you want to know.*

**Deliberate failure:** set the label to a column and then let a duplicate of it be a feature
— a perfect score that means nothing. This previews leakage (1.9).

---

## 1.2 — The five kinds of column

**Diagram:** a column of values shown alongside its detected type, with the legal operations
listed. A type switch lets you see the same values reinterpreted.

**Interaction:** choose a type for the column; the allowed operations and a small preview
chart change with it.

**Text:** numeric, ordinal, categorical, text, and datetime. A number that is really a
category (a zip code, a shirt size) will quietly ruin any distance-based model. The type
decides which chart you use (Track 0), which encoding you need, and which models can eat it.

**So what:** *The type of a column decides everything you can do with it later.*

---

## 1.3 — One-hot encoding

**Diagram:** a category column on the left; the same rows expanded into 0/1 columns on the
right, with the new columns animating out of the original.

**Interaction:** pick the category column; add a new category and watch a column appear; toggle
"drop first column" and see why the duplicate column is a problem.

**Text:** models do arithmetic, so they need numbers. Assigning 1, 2, 3 to red/green/blue
invents an order and a distance that don't exist. One-hot gives each category its own 0/1
column instead — more columns, no fake maths.

**So what:** *Give each category its own yes/no column, or the model will invent an order.*

**Deliberate failure:** the "just number the categories" version, with a scatter plot showing
the fake ordering distorting the geometry.

---

## 1.4 — Missing data

**Diagram:** a table with holes in it, and a small chart of the remaining data under three
strategies side by side: drop rows, fill with mean, fill with median/flag.

**Interaction:** strategy toggle; a "missingness" slider that removes 0–60% of one column.

**Text:** every strategy is a claim about why the value is missing. Dropping rows is safe only
if missingness is random — if it isn't, you delete exactly the people your model most needed.
Filling with the mean shrinks the spread and hides the fact that you guessed.

**So what:** *How you fill a hole is a statement about why the hole is there.*

**Deliberate failure:** missingness correlated with the label — drop the rows and watch the
score improve while the model gets worse in the real world.

---

## 1.5 — Outliers

**Diagram:** a scatter plot with one draggable point. Live readouts: mean, median, std,
and the fitted line's slope.

**Interaction:** drag the outlier point anywhere, including very far out.

**Text:** one point can move the mean, inflate the variance, and tip a regression line. The
median barely notices. The right question is never "is it an outlier" but "is it a mistake,
a rare real thing, or a clue."

**So what:** *An extreme point isn't wrong — but it does change every summary you compute.*

---

## 1.6 — Scaling

**Diagram:** the same 2D data drawn twice: raw axes, and standardised axes. A kNN
classification boundary (or nearest-neighbour circle) drawn on both.

**Interaction:** per-axis unit sliders (multiply one column by 100, 1000, …).

**Text:** if one column is in thousands and another in single digits, distance-based methods
effectively ignore the small one. Scaling doesn't change the information — it changes which
information the model can hear.

**So what:** *Units are a choice, and unscaled units make the choice for you.*

**Deliberate failure:** crank one axis's units and watch the model's accuracy collapse on data
that hasn't changed at all.

---

## 1.7 — Skew and transforms

**Diagram:** a right-skewed column as a histogram, with a log-transform toggle showing the
histogram after the transform, plus a "back-transform" label on the axis.

**Interaction:** skew slider; log / square-root / none toggle.

**Text:** money, counts and durations are almost always skewed. A log transform pulls the tail
in and makes relationships linear that weren't. It is not free: it changes what the numbers
mean, so every prediction has to be converted back.

**So what:** *A log transform doesn't clean the data — it changes the question you're asking.*

---

## 1.8 — Feature engineering

**Diagram:** a table of raw columns beside a set of derived columns, each with the rule that
made it (ratio, difference, date part, bucket, interaction).

**Interaction:** a small "combine two columns" builder; the derived column appears and a
scatter plot shows whether it separates the labels better than either input did.

**Text:** most of the value in real ML is in inventing columns, not choosing models. `price`
and `area` are weaker than `price / area`. A datetime becomes hour-of-day, day-of-week,
is-weekend. An interaction term captures "this only matters when that is true."

**So what:** *A good new column beats a fancier model almost every time.*

---

## 1.9 — Leakage

**Diagram:** a table with a feature that secretly encodes the answer. A pipeline diagram
(split → fit → score) with the split drawn in the wrong place, showing a suspiciously perfect
score, then the corrected version.

**Interaction:** drag the train/test split boundary; toggle "leaked" vs "clean" pipeline.

**Text:** leakage is when information from the future, or from the label, sneaks into the
features. Scaling before splitting, filling missing values using the whole dataset, a
`cancelled_at` column in a churn model, an ID that happens to sort with the label. It never
shows up as an error — it shows up as a great score that fails in production.

**So what:** *If your model is suspiciously good, look for a feature that already knows the answer.*

**This is the most valuable page in Track 1.** Build it early.

---

## Track 1 exit test

1. Your column is "shirt size: S/M/L." What type is it, and what encoding does it need?
   *(ordinal — one-hot loses the order, label-encoding preserves it; the answer is "ordinal,
   encoded in order")*
2. 20% of a column is missing and it's not missing at random. What's the risk of dropping rows?
3. You multiply one column by 1000. Does your model's accuracy change? Why or why not?
4. You have `order_date` as a raw timestamp. Name three features you'd derive from it.
5. Your model scores 0.99. What's the first thing you check?

---

## Where Track 1 ends and Track 2 begins

Track 1 is *make each column good*. Track 2 is *decide which columns to keep* — which only
makes sense once every column is on the same footing and correctly encoded.
