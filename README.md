# 🦇 Batcomputer ML — Interactive Machine Learning Explainer

An interactive, single-page web experience that teaches the full machine learning workflow through the lens of a real-world industrial classification problem. Built to make ML concepts accessible to non-technical audiences while preserving technical accuracy.

**Live demo:** _[add your deployment URL here]_

---

## Overview

Most ML tutorials either oversimplify to the point of being useless or assume a graduate-level background. This project takes a different approach: it walks a complete, real ML pipeline — from raw data to a deployed decision threshold — using an extended narrative analogy (a detective investigating suspects) to anchor each technical concept.

The experience is built around a genuine quality-engineering problem: distinguishing good automotive Hall-effect current sensors from defective ones that pass an internal tester but fail a stricter downstream customer test. The dataset, the failure mode, and the trade-offs are real.

---

## The problem it teaches

A batch of **462 sensors** all pass the internal 20A test, yet **142 of them fail** the customer's stricter 220A validation. The challenge: build a model that catches the defective units *before* they reach the customer, where an escaped defect is far more costly than a falsely rejected good part.

This frames the single most important lesson in applied classification: **accuracy is not the goal — catching what actually matters is.** A model can be 69% accurate by labeling everything "good" and still be worthless, because it never catches a single defect.

---

## What the experience covers

The site is structured as a scrollable, chapter-based narrative. Each chapter pairs a plain-language explanation with the corresponding real Python code.

| Chapter | ML concept | Covered topics |
|---|---|---|
| The Case File | Data fundamentals | Datasets, features, labels, class imbalance |
| Studying the Scene | Exploratory Data Analysis | Histograms, boxplots, outlier detection (IQR), correlation matrices |
| Cleaning the Evidence | Preprocessing | Standardization (z-score), train/test split, data leakage |
| Training the Detective | Modeling | The `fit → predict → evaluate` pattern, logistic regression |
| The League of Detectives | Advanced models | Decision Trees, Random Forest, XGBoost, SVM (RBF kernel) |
| The Paranoia Dial | Decision threshold | Precision/recall trade-off, confusion matrix, business-cost-driven thresholding |
| Case Closed | Key takeaways | Interpretability vs. accuracy, model selection with limited data |

---

## Key interactive features

- **Live decision-threshold slider** — Users drag between "paranoid" and "relaxed" detection modes and watch the confusion-matrix outcomes (caught defects, escaped defects, false rejections, recall) update in real time. This makes the precision/recall trade-off tangible rather than abstract.
- **Flip-card model comparison** — Each advanced model is presented as an interactive card explaining its mechanism, strengths, and a code snippet.
- **Scroll-triggered animations** — Each chapter animates into view to support the narrative pacing.
- **Copy-ready code snippets** — Every concept is paired with the actual Python that implements it, with syntax highlighting and copy-to-clipboard.

---

## Concepts a reviewer can verify I understand

This project is intentionally designed to demonstrate not just coding ability but **applied ML judgment**:

- Why **class imbalance** makes raw accuracy misleading, and why recall on the minority (defect) class is the metric that matters here.
- How **data leakage** sneaks in through improper scaling or feature selection, and how `fit` on train / `transform` on test prevents it.
- Why **decision thresholds are a business decision, not a default** — in automotive quality, the cost of an escaped defect dwarfs the cost of a false rejection, which justifies a lower threshold.
- Why **more complex models don't automatically win** — with only a few hundred samples, a simple, interpretable Decision Tree can outperform XGBoost in practice, and interpretability itself has value when you must justify a decision to a customer.

---

## Tech stack

- **Framework:** React + Vite
- **Styling:** Tailwind CSS
- **Animations:** CSS transitions / scroll-triggered reveals
- **Design system:** Custom "Gotham Noir" theme (dark palette, single accent color, condensed display typography)

---

## Design approach

The visual language is deliberately restrained: a deep near-black background, a single high-contrast accent color used sparingly for emphasis, and clear typographic hierarchy. The goal was a focused, atmospheric reading experience that keeps attention on the content rather than competing with it — the same design discipline applied in production dashboards and data tools.

---

## Running locally

```bash
# Clone the repository
git clone https://github.com/<your-username>/batcomputer-ml.git
cd batcomputer-ml

# Install dependencies
npm install

# Start the dev server
npm run dev
```

The site will be available at `http://localhost:5173`.

---

## About the dataset

The underlying data comes from a real automotive quality-engineering investigation into Hall-effect current sensors. All customer-identifying information has been removed. The dataset is used here strictly for educational demonstration of the ML workflow.

---

## Background

Built as a portfolio piece bridging quality engineering and AI engineering. The project reflects hands-on experience taking an industrial classification problem through the full lifecycle — data analysis, preprocessing, model comparison, and threshold tuning driven by real business cost asymmetries — and then communicating that workflow clearly to a non-technical audience.

---

## License

MIT — feel free to learn from, fork, and build on this.
