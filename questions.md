# Open Questions

Each one changes what gets built. Answer them inline (`→ answer`) and I'll fold the answers
into `roadmap.md`. Ordered by how much they block.

---

## A. Scope and audience

**A1. Who is the reader, precisely?**
v0.1 said "high school students, 13–18." But "teach feature engineering and selection" is
undergrad/early-practitioner material. These are different readers with different patience.
- (a) Curious beginner who has never opened a spreadsheet
- (b) Student who can use Excel but has never coded
- (c) Someone who can write `pandas` code but doesn't know *why* to scale or select
- (d) All three, with each page written to be readable by (a) and not boring to (c)

→ 

**A2. Does the reader write any code?**
Options: no code at all (pure visual) · pseudocode only · real Python shown but not required
· interactive Python (Pyodide in the browser).
This decides whether pages are HTML-only or need a code panel.

→ 

**A3. How long should one concept page take?**
My assumption: 2–3 minutes of reading, 1–2 minutes of playing. If you want 10-minute deep
dives, the pages double in size and the track shrinks.

→ 

**A4. Is this for you to teach with (projected in a class, you narrating), or for someone to
use alone with no explanation?** A teacher-driven tool can have terse labels and let you talk.
A self-serve tool has to say everything.

→ 

## B. Content ordering

**B1. Track 0 is 10 pages and has no models in it at all.** Is that the right first release —
a "how to read data" tool that never mentions ML — or does page one need to promise where
this is going?

→ 

**B2. Your message says "teach the graphs and how to display data first."** Do you mean
*statistical* display (histograms, box plots, correlation) or *chart-making* (which chart type
for which data)? I assumed both, statistical first. Correct?

→ 

**B3. Where does statistics end and ML begin for you?** Mean/median/variance, distributions,
correlation — these are Track 0 material in my plan. Should the tool also cover probability
basics (Bayes, sampling, the normal distribution) before models, or is that out of scope?

→ 

**B4. Do you want a level on *reading a model's output* (confusion matrix, precision/recall,
ROC, residuals) as its own track, or folded into Track 3?** I lean toward its own mini-track
after Track 3, because "the model is 94% accurate" is the most misleading sentence in the
field and deserves diagrams.

→ 

## C. The diagram mechanics

**C1. SVG vs. Canvas.** SVG makes each element inspectable and CSS-styleable; Canvas is better
past ~5,000 points. My default is SVG, with Canvas only for the "too many points" page (0.6).
Agree?

→ 

**C2. Do you want to use a charting library (D3, Chart.js, Observable Plot) or hand-rolled SVG?**
Hand-rolled means no dependency and full control, but slower to build and each chart type
must be written from scratch. D3 is the standard but has a real learning curve.

→ 

**C3. Which datasets?** Real ones (Iris, Titanic, Palmer Penguins, a small housing set) or
synthetic-only? Real data is more credible; synthetic data is cleaner and lets me construct
exact teaching cases. My plan: synthetic for mechanism pages, one real dataset recurring
across the whole tool so the reader watches the same data get better and better.

→ 

**C4. Does "live" mean draggable?** I'm assuming yes — the reader can drag a point and watch
the mean move, drag a bin edge and watch the histogram change. That's most of the build cost.
If you'd accept sliders and buttons only, this gets much cheaper.

→ 

## D. Product shape

**D1. You said no proper save. Confirm there is truly no persistence** — no progress, no
"completed" marks, no bookmarks. Just a hub page and prev/next links. (I've planned it that
way; say so if you want even a "last visited" link.)

→ 

**D2. Single HTML file for the whole tool, or one file per concept?** v0.1 locked "single
self-contained HTML file." That was for the game. For ~30 concept pages, one file becomes
unmaintainable. My plan: one file per concept + one hub file, all shareable by link.

→ 

**D3. Where does it live?** GitHub Pages on this repo (so `mike-franco.github.io/machineLearningEZ`
works), or does it stay local files you open?

→ 

**D4. Pixel art — keep it?** v0.1 locked retro pixel with "Press Start 2P". That font is
genuinely hard to read at body size, and it fights with chart axis labels. Options: keep pixel
for headings only · keep the palette, use a clean font · drop it entirely for a
data-viz-appropriate look (dark background, muted grid, one accent colour).

→ 

## E. Working together

**E1. Do you want to answer these first, or should I build the reference page (0.2 scatter) so
you can react to something concrete?** Some of these are easier to answer with a page in front
of you.

→ 

**E2. Commit directly to `main`, or open a branch + PR per chunk?**

→ 
