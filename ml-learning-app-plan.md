# ML Quest — Gamified Machine Learning Learning App

> Plan draft v0.1 — created 2026-11-23

---

## 1. Vision & Audience

**Goal:** Teach high school students (ages 13–18) what machine learning models are and *intuitively how they work*, through play — not lectures.

**Design principles**

- **Visual before math** — every model is explained with an interactive demo first; the math appears only as optional "deep dive" unlocks.
- **Learn by doing** — the player never just reads; they drag data points, draw boundaries, and make predictions.
- **Collection mindset** — models are unlockable "tools/creatures," giving players a reason to keep going (like a Pokédex).

---

## 2. The Game Concept

**Story frame:** The player is a **Model Trainer**. Each dataset is a *world* to explore, and each ML model is a *tool* they unlock, train, and use to solve challenges.

**Core loop (repeated for every model):**

1. **Discover** — short animated story beat introducing the model ("Meet kNN: the copy-your-neighbors guesser")
2. **Playground** — interactive sandbox (drag points, move sliders, watch the model learn live)
3. **Challenge** — a mini-game where the player *uses* the model to score points
4. **Prove it** — quick quiz (3–5 questions) to "Master" the model
5. **Reward** — XP, level-up, badge, model added to the collection

**Progression systems**

- XP & levels
- **ModelDex** — collection of mastered models
- Badges & achievements (e.g. "Boundary Drawer," "Tree Whisperer")
- Streaks / daily quests
- **Boss challenges** — real datasets (Titanic, Iris) where the player picks which model to deploy

---

## 3. Learning Objectives

By the end, the player can:

- Explain the difference between classification and regression
- Explain in plain words what kNN, Linear Regression, Logistic Regression, Decision Trees, Naive Bayes, SVM, and (intro-level) Neural Networks do
- Pick an appropriate model for a simple problem
- Understand the ideas of training data, prediction, overfitting (introduced gently via gameplay), and accuracy

---

## 4. Content Map — Models in Teaching Order

| # | Model | One-liner for kids | Gamified mini-game idea |
| --- | --- | --- | --- |
| 1 | **kNN** | "Guess by asking your nearest neighbors" | Place new creature on a map; vote of the K closest friends decides its type |
| 2 | **Linear Regression** | "Draw the best line through the dots" | Draw a line by hand; game scores how close your line is to the perfect fit |
| 3 | **Logistic Regression** | "One line that separates two teams" | Draw a boundary to separate cats from dogs; see how many you got right |
| 4 | **Decision Trees** | "A game of 20 questions" | Play 20 questions against the tree; watch it build the questions from data |
| 5 | **Naive Bayes** | "The spam detective" | Sort messages into inbox vs spam; learn why words are clues |
| 6 | **SVM** | "Draw the widest road between two crowds" | Widen the margin; see why a bigger gap = safer guesses |
| 7 | **Neural Network** (intro) | "A brain made of layers of switches" | Teach a network to recognize your doodles |

---

## 5. Lesson Template (reused for every model)

Each model module contains:

1. **Hook** — 30-second story/animation (why this model exists)
2. **Intuition demo** — interactive visualization
3. **Playground** — sandbox with sliders/draggable data
4. **Challenge game** — score-based mini-game
5. **Quiz** — 3–5 questions to master the model
6. **Deep dive (optional)** — the actual math, for curious players

---

## 6. Tech Stack — Options (decision needed)

| Option | Tools | Pros | Cons |
| --- | --- | --- | --- |
| **A. Web app** | React/Next.js + TensorFlow.js or ml5.js, D3 for visuals | Runs anywhere, easy to share, real ML in-browser | Needs web dev skills |
| **B. No-code** | Glide, FlutterFlow, Softr | Fast to build, no coding | Limited interactive demos |
| **C. Game engine** | Godot or Unity | Feels like a real game | Overkill for data viz; harder to embed real ML demos |

**Recommendation:** Option A (web app) — ML demos can run live in the browser, which is the heart of this app.

---

## 7. MVP Scope (build this first)

- 3 models: **kNN, Decision Trees, Linear Regression**
- 1 dataset playground per model (synthetic, kid-friendly data)
- Core loop: demo → game → quiz → XP
- XP + levels + ModelDex (simple versions)
- 1 boss challenge (Iris dataset: "pick the right model")

---

## 8. Roadmap

| Phase | Deliverable |
| --- | --- |
| **0. Decide** | Lock platform, tools, art style; write full content script for 3 MVP models |
| **1. Prototype** | One model end-to-end (kNN) — demo, game, quiz, XP — to test the fun factor |
| **2. MVP** | All 3 MVP models + progression systems |
| **3. Playtest** | 5–10 high schoolers; watch where they get bored or confused |
| **4. Iterate** | Fix pain points; polish |
| **5. Expand** | Add remaining models (LogReg, Naive Bayes, SVM, intro NN), more boss challenges, leaderboards |

---

## 9. Decisions (locked 2026-11-23)

| Question | Decision |
| --- | --- |
| Platform | **Web app** |
| Build approach | **Kimi builds it** — user takes the finished code; zero coding required from user |
| Art style | **Retro pixel** (8-bit, NES-style palette, "Press Start 2P" font) |
| Team | Solo project |
| Course tie-in | Not tied to Orange/sklearn/PyCaret labs — but it teaches the same concepts |
| Login | Single-player, offline, progress saved in browser (localStorage) |

**Tech:** single self-contained HTML file per build (no build step, runs anywhere), Canvas games, vanilla JS, pixel font.

## 10. Build Log

| Date | What happened |
| --- | --- |
| 2026-11-23 | Plan v0.1; decisions locked; Phase 1 prototype → **kNN level** (dialogue → playground → challenge game → quiz → XP + ModelDex) |

*Next step: playtest kNN prototype, then build MVP model #2 (Decision Trees).*
