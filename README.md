# Explainable AI — Breast Tumour Classification (LIME, LORE, SHAP)

Course project for **EXplainable Artificial Intelligence** (University of Pisa, PhD programme),
3 March 2024 — **joint work by Gurban Aliyev, Tsewalo Tondji Idriss Cabrel and Arman Zafaranchi**.

The project studies *why* a black-box classifier makes a given prediction. We train a small neural
network to distinguish benign from malignant breast tumours, then apply post-hoc explanation
methods to individual predictions and compare them with inherently interpretable models.

> **Note:** this repository contains the project **report and presentation only** — the course
> deliverable was the written analysis, not a code submission.

## Setting

- **Dataset:** [Breast Cancer Wisconsin (Diagnostic)](https://doi.org/10.24432/C5DW2B) (UCI) —
  569 instances (357 benign, 212 malignant), 30 numeric features describing cell-nucleus images,
  no missing values.
- **Black-box model:** a simple feed-forward neural network in PyTorch —
  **92.98 % accuracy, 84.31 % precision, 100 % recall, F1 91.49 %**.

## Explanations

Ten instances are selected across three regimes — misclassified, low-confidence, high-confidence —
and explained with:

- **LIME** — local surrogate model from perturbations around the instance.
- **LORE** — local rule-based explanations plus counterfactual rules.
- **SHAP** — additive Shapley-value attributions (beeswarm / waterfall / force plots).

For the dataset at hand, features such as `area-worst`, `area-mean` and `area-se` dominate the
malignancy decisions, while `perimeter-mean` and `texture-worst` act in the opposite direction.

## Interpretable models

We also train inherently interpretable models on the same data — a **logistic regression** (log-odds
coefficients per feature) and a **decision tree** (via InterpretML) — to compare their transparency
against the post-hoc explanations. Fidelity of the interpretable model to the black box, measured on
the ten instances, was **50 %** — a useful reminder that local explanations need not transfer to a
faithful global surrogate.

## Repository contents

```
report/xai_breast_tumor_explainability_report.pdf   # project report
slides/xai_presentation.pptx                        # presentation
slides/xai_presentation_speech.docx                 # speaker notes / script
```

## Reference

F. Bodria, F. Giannotti, R. Guidotti, F. Naretto, D. Pedreschi, S. Rinzivillo,
"Benchmarking and survey of explanation methods for black box models,"
*Data Mining and Knowledge Discovery*, 2023.
