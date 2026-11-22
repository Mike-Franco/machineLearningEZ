# Page Template

The spec every concept page follows. If a page deviates, it should be for a reason worth
writing down here.

---

## Structure, top to bottom

```
┌──────────────────────────────────────────────┐
│  ML EZ   Track 0 · Reading Data    ← hub     │   thin header, no nav menu
├──────────────────────────────────────────────┤
│                                              │
│  0.2  Scatter plots                          │   number + concept name
│  Two columns become a shape.                 │   one-line promise
│                                              │
├──────────────────────────────────────────────┤
│                                              │
│   ┌────────────────────────────────────┐     │
│   │                                    │     │
│   │        THE LIVE DIAGRAM            │     │   ~45% of viewport height
│   │        (controls below it)         │     │   controls sit under, not beside
│   │                                    │     │
│   └────────────────────────────────────┘     │
│   [ x: bill_length  ▾ ]  [ y: flipper ▾ ]    │
│                                              │
├──────────────────────────────────────────────┤
│                                              │
│  Two short paragraphs. Plain words. No       │
│  bullet-point dumps. One idea per           │
│  paragraph.                                  │
│                                              │
│  A second paragraph, or a small table, if    │
│  there is genuinely a second thing to say.   │
│                                              │
│  ▸ Show the formula            (collapsed)   │   optional, closed by default
│                                              │
├──────────────────────────────────────────────┤
│  In one line: each dot is one row, and the   │   the "so what" — visually distinct
│  position is just two of its columns.        │
├──────────────────────────────────────────────┤
│  ← 0.1 What data is        0.3 Histograms →  │   prev / next
└──────────────────────────────────────────────┘
```

## Rules

**The diagram comes before the words.** Not beside, not after. The reader must be able to
see the thing before being told what it is. This is the whole reason the tool exists.

**The diagram is interactive in exactly one way.** One page teaches one gesture: drag a point,
or move a slider, or toggle a layer. Two gestures means two ideas and the page is split.
"Reset" is always available; nothing else is a button.

**No scrolling to see the diagram and the controls together.** If the reader has to scroll
between moving a slider and seeing its effect, the page is broken.

**Paragraphs, not bullets.** Bullets are where explanations go to die. Two to four short
paragraphs. If a list is genuinely the right shape (the five summary numbers in a box plot),
use a small table instead.

**The formula is collapsed.** A `<details>` block labelled "Show the formula." Nobody is
blocked by it; nobody is scared by it.

**The "so what" is one sentence,** in the reader's words, repeatable to a friend. It is the
test of whether the page is finished. Styled differently from body text — a box, or an accent
left-border.

**No navigation beyond prev/next and back-to-hub.** No sidebar, no search, no progress bar.

## Technical conventions

- **One self-contained file.** HTML, CSS and JS in one `.html`. No CDN links, no build step.
  It must work opened from `file://`.
- **SVG for the diagram.** Hand-rolled, no library. Elements get `data-*` hooks so they can
  be inspected. Canvas only for the high-density page (0.6).
- **Colours in CSS custom properties** at the top of the file, so the whole tool can be
  re-themed from one place. If pixel art survives, the palette lives here.
- **Axis labels always present**, with units. A chart without an axis label is a decoration.
- **Reduced motion respected.** `prefers-reduced-motion` turns off transitions and animations.
- **Keyboard accessible.** Anything draggable also moves with arrow keys; controls are real
  `<input>` elements.
- **Touch works.** `pointerdown/pointermove/pointerup`, never mouse-only events.
- **No external fonts** if pixel art is dropped; system font stack otherwise.
- **File naming:** `concepts/<track>.<index>-<slug>.html`, e.g. `concepts/1.9-leakage.html`.
- **The hub** is `index.html` and lists all four tracks from a small inline JS array, so
  adding a page is a one-line change.

## Page checklist before it counts as done

- [ ] The diagram renders with real axes, ticks and units
- [ ] The one interaction works with mouse, touch and keyboard
- [ ] Reset works and restores the initial state exactly
- [ ] Two to four paragraphs, no bullets, no jargon used before it's defined
- [ ] The "so what" sentence exists and is genuinely repeatable
- [ ] Formula collapsed, and correct
- [ ] Prev/next links point at the right pages
- [ ] Opens from `file://` with no console errors
- [ ] Readable at 375px wide (phone) and at 1440px
- [ ] A deliberate failure or edge case is shown somewhere on the page
