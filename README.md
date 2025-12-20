**Focus:** Regression Universe, Bias–Variance Tradeoff & Regularization  
---

## 📌 Project Overview

This project provides a **systematic exploration of regression models** for continuous
prediction, with a strong emphasis on **bias–variance tradeoff, regularization, and model
stability**.

Rather than optimizing a single metric, the project evaluates **how and why different
regression models behave**, using cross-validation and multiple error metrics to draw
robust conclusions.

---

## 📊 Dataset

**Energy Efficiency Dataset (UCI Repository)**

- Task: Predict **Heating Load**
- Features:
  - Relative Compactness
  - Surface Area
  - Wall Area
  - Roof Area
  - Overall Height
  - Orientation
  - Glazing Area
  - Glazing Area Distribution
- Characteristics:
  - Clean, low-noise
  - Structured physical relationships
  - Mild non-linearity and feature interactions

---

## 🎯 Learning Objectives

- Understand **regression error metrics** and their meaning
- Diagnose **bias vs variance** in continuous prediction
- Evaluate **regularization techniques**
- Visualize **underfitting and overfitting**
- Compare parametric, kernel-based, and tree-based regressors
- Learn when flexibility helps — and when it hurts

---

## 📐 Evaluation Metrics

All models are evaluated using **5-fold cross-validation**.

| Metric | Meaning |
|-----|-----|
| MAE | Average absolute error |
| MSE | Penalizes large errors |
| RMSE | Error in original target units |
| R² | Variance explained by the model |

> **RMSE + R² together** provide the most reliable picture.

---

## 🧠 Modeling Roadmap

### Step 1 — Linear Regression (Baseline)
- High bias, low variance
- Establishes performance floor

### Step 2 — Regularized Linear Models
- **Ridge (L2):** coefficient shrinkage
- **Lasso (L1):** feature selection
- **ElasticNet:** balance of L1 and L2

Purpose:
> Test whether the problem is variance-limited at the linear level.

### Step 3 — Polynomial Regression
- Explicit non-linearity
- Degree sweep to expose bias–variance curve
- Ridge regularization to stabilize overfitting

### Step 4 — Support Vector Regression (SVR)
- Margin-based regression
- ε-insensitive loss
- Linear vs RBF kernel comparison

### Step 5 — Random Forest Regressor
- Non-parametric, bagging-based regression
- Captures complex interactions
- Examines stability vs average accuracy

---

## 📊 Final Model Comparison (Cross-Validated)

| Model | RMSE (Mean) | RMSE (Std) | R² (Mean) | Key Insight |
|----|----|----|----|----|
| Linear Regression | 3.166 | 0.463 | 0.890 | Bias-limited baseline |
| Ridge Regression | 3.172 | 0.466 | 0.890 | Regularization unnecessary |
| Lasso Regression | 3.227 | 0.469 | 0.886 | Sparsity increases bias |
| ElasticNet | 3.273 | 0.505 | 0.882 | Over-regularization |
| **Polynomial (Degree 2)** | **1.476** | 0.885 | **0.967** | Best bias–variance balance |
| Polynomial (Deg ≥ 3) | ❌ Explodes | ❌ | ❌ | Severe overfitting |
| Poly (Deg 5 + Ridge) | 2.173 | 0.726 | 0.942 | Regularization rescues instability |
| Linear SVR | 3.135 | 0.525 | 0.891 | Similar to linear regression |
| RBF SVR | 1.632 | 0.583 | 0.967 | Smooth non-linear fit |
| **Random Forest Regressor** | **1.229** | **1.175** | 0.965 | Lowest RMSE, high variance |

---

## 🧠 Key Insights

- Linear models are **bias-limited**, not variance-limited
- Regularization does **not** help when coefficients are already stable
- Polynomial degree 2 captures essential physical interactions
- Higher-degree polynomials cause **numerical and statistical instability**
- SVR captures smooth non-linearity with strong stability
- Random Forest achieves the lowest average error but suffers from **high variance**
- Model choice depends on **stability vs accuracy**, not leaderboard performance

---

## 🏁 Final Conclusion

This project demonstrates that **regression performance is governed by alignment between
model assumptions and data structure**.

For the Energy Efficiency dataset:
- The underlying relationship is **smooth and low-degree**
- Moderate non-linearity provides the best generalization
- Excessive flexibility leads to instability rather than improvement

> **The best model is not the most powerful one —  
> it is the one whose complexity matches the data.**

---

**Author:** Tanveer Singh  
**Focus:** Core Machine Learning Foundations
