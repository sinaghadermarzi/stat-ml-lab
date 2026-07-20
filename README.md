# Stat-ML Lab — Senior DS/Applied Scientist Interview Learning Lab

A hands-on curriculum of executed Jupyter notebooks covering the topics that actually come up
in **senior data scientist / applied scientist interviews** — and in the highest-impact
real-world applications of data science: product & business analytics, experimentation,
finance, and operations.

**Who it's for.** You already know core probability, statistics, and machine learning.
These notebooks skip the basics and go straight to the applied, senior-level material:
the nuances, the pitfalls, the trade-offs, and the "how it's really done in industry."

**How it teaches.** Every notebook is a set of hands-on experiments — mostly simulations
with known ground truth, so you can *verify* that methods work (and watch them fail when
their assumptions break). Each ends with an **Interview corner** (realistic questions with
strong-answer outlines), **key takeaways**, and **exercises with solutions**.

## Setup

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Python ≥ 3.10 recommended. The two PySpark notebooks additionally need a Java runtime
(Java 17 or 21). Every notebook runs end-to-end in a few minutes on a laptop; all randomness
is seeded so you'll reproduce the committed outputs.

## Curriculum

<!-- CURRICULUM_INDEX -->

## Suggested paths

- **Product DS / tech company interview:** modules 01 → 02 → 03 → 07 → 08, then 06.
- **ML-heavy applied scientist:** modules 01 → 04 → 05 → 10, then 02 → 03.
- **Finance / operations:** modules 01 → 05 → 09, then 04 → 06.

## Contributing

See [STYLE.md](STYLE.md) for the notebook structure and quality bar.
