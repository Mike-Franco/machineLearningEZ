# Track 0 — Reading Data

The foundation track. Ten pages, no models, no code. By the end the reader can look at a
table and see the shape of it, and knows which chart answers which question.

This track alone is a useful, shareable artifact — it stands on its own even if nothing else
gets built.

---

## 0.1 — What data is

**Diagram:** a small table (5 rows × 3 columns, penguins-ish) on the left; the same table on
the right with one row highlighted and its three values pulled out as a labelled record.

**Interaction:** click any row; it highlights and the record panel updates.

**Text:** rows are examples, columns are measurements. Nothing else. The word "dataset" is
just "all the rows."

**So what:** *A dataset is a table, and every row is one thing you measured.*

---

## 0.2 — Scatter plots  ← the reference page, build this first

**Diagram:** the same penguin data as points. Two dropdowns under it choose which column is
x and which is y. Switching columns re-plots with a smooth transition.

**Interaction:** the two column pickers. Plus hovering a point shows its row.

**Text:** two columns, mapped to horizontal and vertical position, and you can suddenly see
a relationship that was invisible in the table.

**So what:** *A scatter plot is two columns of a table, and nothing else.*

---

## 0.3 — Histograms and distributions

**Diagram:** one numeric column as a histogram, with a bin-width slider. A mean line and a
median line sit on top and visibly separate as the data skews.

**Interaction:** bin-width slider; toggle mean/median markers.

**Text:** a histogram is a scatter plot where one axis got replaced by "how many." Bin width
is a choice you make, and it changes the story. The mean chases the tail; the median doesn't.

**So what:** *A histogram counts things, and how you count them is up to you.*

**Deliberate failure:** at bin width = 1 the shape is noise; at width = the whole range it's
a single bar. Show both extremes.

---

## 0.4 — Box plots

**Diagram:** the same column drawn twice — as a histogram and as a box plot beneath it — so
the five numbers map visibly onto the shape.

**Interaction:** drag the quartile boundaries on the box and watch the histogram region they
enclose highlight.

**Text:** five numbers (min, Q1, median, Q3, max) summarise a column, and the box is the
middle half. Box plots compare many columns at once where histograms can't.

**So what:** *A box plot is a column boiled down to five numbers.*

---

## 0.5 — Relationships and correlation

**Diagram:** a scatter plot where you can drag points, with a best-fit line and an `r` value
that updates live.

**Interaction:** drag points freely. Drag them into a tight line, into a circle, into a
curve — watch `r` respond.

**Text:** correlation measures direction and tightness, not steepness and not cause. A curve
can have `r ≈ 0` while being perfectly predictable — the line is the wrong tool.

**So what:** *Correlation is how tightly points hug a straight line — and nothing about why.*

**Deliberate failure:** a clear U-shape with `r = 0`. This is the page's punchline.

---

## 0.6 — Too many points

**Diagram:** a Canvas scatter plot whose point count ramps from 50 to 50,000. A toggle for
opaque vs. semi-transparent points, and one for a density (hexbin) view.

**Interaction:** count slider; opacity toggle; density toggle.

**Text:** past a few thousand points, a scatter plot stops showing density and starts showing
a solid blob. Alpha and binning are how you get the structure back.

**So what:** *With enough points, every scatter plot looks the same — until you change how you
draw it.*

---

## 0.7 — Charts that lie

**Diagram:** a single small dataset with four broken charts and a "fix it" toggle each:
truncated y-axis, dual y-axes, 3D-ish pie, and a line chart of unordered categories.

**Interaction:** four independent toggles, each switching one chart between broken and honest.

**Text:** the numbers are identical in both versions of each chart; only the drawing changes.
Every one of these appears in real newspapers and real slide decks.

**So what:** *The same data can be drawn to say opposite things, and the numbers won't warn you.*

---

## 0.8 — Categories and groups

**Diagram:** the same category counts shown three ways: bar chart, pie chart, and a stacked
bar. A toggle for "compare groups" that adds a second categorical split.

**Interaction:** chart-type toggle; add/remove a grouping variable.

**Text:** bars compare; pies show parts of a whole (and fail past ~4 slices). Grouped bars let
you ask a second question of the same data.

**So what:** *Pick the chart by the question: comparing values wants bars, splitting a whole
wants a pie.*

---

## 0.9 — Time series

**Diagram:** a line chart of a monthly series with noise. A rolling-average window slider
overlays a smoothed line.

**Interaction:** window slider; toggle the raw series.

**Text:** when the x-axis is time, order carries meaning that a scatter plot throws away. A
rolling average is the simplest way to see a trend through noise — and the window size is
again a choice that changes the story.

**So what:** *If the order of the rows matters, the chart must show order.*

---

## 0.10 — Too many columns

**Diagram:** a scatter-matrix (small multiples) of 4 numeric columns — 6 pairwise plots — with
one cell enlarged on hover.

**Interaction:** hover to enlarge; a toggle switches to a correlation heatmap of the same data.

**Text:** a screen can show two dimensions well and three badly. Beyond that you tile pairs,
or you summarise the pairs as a grid of correlations. Either way you are choosing what to hide.

**So what:** *You can only see two columns at once — so the rest become a grid or a number.*

**This page sets up Track 1:** the reason features matter is that you can't look at all of
them, so you have to choose and prepare them well.

---

## Track 0 exit test

The reader should be able to answer, without the tool:

1. Which chart would you use to compare the median income of five cities? *(box plot or bars)*
2. What does it mean if a scatter plot shows `r = 0`? *(no straight-line relationship — but
   possibly a strong curved one)*
3. Your scatter plot is a solid blob. What are two ways to fix it? *(alpha, density/hexbin)*
4. Why does the mean move when one point is dragged far away, but the median barely does?
5. You have eight numeric columns and want to see their relationships. What do you do?
   *(scatter matrix or correlation heatmap — and accept that you're hiding things)*

If those land, Track 0 is done.
