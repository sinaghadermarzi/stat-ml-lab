# Notebook Style Guide

This guide defines the structure and quality bar for every notebook in this learning lab.
Follow it when contributing or extending notebooks.

## Audience

Senior applied scientist / data scientist interview candidates. Assume the reader already
knows core probability, statistics, and ML. Do **not** re-teach basics (what a p-value is,
what overfitting is). Go straight to the applied, senior-level material: nuances, pitfalls,
trade-offs, and how things are actually used in industry (product/business analytics,
finance, operations).

## Notebook structure (required sections, in order)

1. **Title cell** (markdown): `# <Topic>` followed by:
   - *What you'll learn* — 3–6 bullets, specific and outcome-oriented.
   - *Why it matters in interviews* — 2–4 bullets naming the kinds of questions this topic shows up in.
2. **Setup cell**: all imports at the top, a single seeded RNG (`rng = np.random.default_rng(42)`),
   matplotlib defaults. No hidden state.
3. **Concept sections**: each major concept gets a markdown explanation followed by
   hands-on code. Simulation with known ground truth is preferred wherever the point is
   inferential (you can *check* the method recovers the truth).
4. **Pitfalls section**: the mistakes practitioners actually make with this topic, each
   demonstrated in code where feasible, not just described.
5. **Interview corner** (markdown): 4–8 realistic interview questions on this topic with
   concise strong-answer outlines (what a senior candidate should hit).
6. **Key takeaways**: 5–10 bullets.
7. **Exercises**: 2–4 exercises with solutions (solutions in code cells directly below,
   clearly marked `# --- Solution ---`).

## Code standards

- Deterministic: seed everything (`np.random.default_rng(42)`; pass `random_state=42` /
  `seed=42` to libraries). A fresh top-to-bottom run must reproduce all outputs.
- The notebook must execute cleanly top-to-bottom in **under ~4 minutes** on a small machine.
  Keep simulations and MCMC draws sized accordingly (this is a learning lab, not a benchmark).
- No unhandled warnings spam: fix the cause where possible rather than suppressing globally.
- Plots: every plot has a title and axis labels. Prefer matplotlib/seaborn defaults; keep
  figures readable, not decorative.
- Pandas: idiomatic, no chained-assignment patterns, no deprecated APIs.
- No internet at run time except the whitelisted dataset sources below, and always through
  the caching helper pattern (check `data/` first, download only if missing).

## Data policy

- **Simulation first** for anything inferential/causal — you need ground truth to show a
  method works (or fails). Make simulations *realistic*: name variables after business
  quantities (sessions, conversion, GMV, churn), use plausible magnitudes.
- Real datasets, when they add value, come from:
  - `sklearn.datasets` (bundled loaders and `fetch_california_housing`)
  - `seaborn.load_dataset(...)` (tips, diamonds, flights, penguins, taxis…)
  - `statsmodels.api.datasets` (co2, macrodata, sunspots…)
- Small downloaded files (≤ 2 MB) are cached to `data/` and committed. Anything larger is
  download-on-run only.

## Tone

Direct, practical, and opinionated where practice has converged (e.g., "use time-based
splits for time-ordered data — random K-fold leaks"). Explain *why*, show the failure mode
in code, then the fix. Cross-reference sibling notebooks rather than duplicating material.
