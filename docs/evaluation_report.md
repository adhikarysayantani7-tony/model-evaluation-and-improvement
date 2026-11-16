# Model Evaluation & Performance Improvement Report

## 1. Performance Comparison Table

| Model Configuration | Train Accuracy | Test Accuracy | Precision | Recall | F1-Score | Diagnosis |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Decision Tree (`max_depth=1`)** | ~92.3% | ~89.5% | ~90.1% | ~93.1% | ~0.916 | **Underfitting** (High Bias) |
| **Decision Tree (`max_depth=None`)** | 100.0% | ~91.2% | ~95.6% | ~90.3% | ~0.929 | **Overfitting** (High Variance) |
| **Random Forest (`max_depth=5`)** | ~99.3% | ~95.6% | ~95.9% | ~97.2% | ~0.966 | **Improved Ensemble** |
| **Logistic Regression (Scaled + L2)** | ~98.9% | **~98.2%** | **~98.6%** | **~98.6%** | **~0.986** | **Best Generalization** |

---

## 2. Metric Selection Rationale
* **Accuracy**: Measures overall correct predictions, useful as a baseline since the dataset is reasonably balanced.
* **Recall (Sensitivity)**: Critical in medical screening (Breast Cancer dataset) because missing a malignant case (false negative) is far more costly than a false alarm.
* **Precision & F1-Score**: Ensures high recall does not come at the expense of excessive false positives; F1-Score balances both metrics into a single reliable benchmark.
* **ROC-AUC**: Evaluates how well the model separates classes across all probability thresholds.

---

## 3. Model Strengths & Weaknesses

### A. Decision Tree (`max_depth=1` vs. `max_depth=None`)
* **Strengths**: Easy to visualize and requires no feature scaling.
* **Weaknesses**: At `max_depth=1`, the tree **underfits** by missing multi-feature interactions. At `max_depth=None`, it memorizes training noise (100% train accuracy) and **overfits**, dropping sharply on test data.

### B. Regularized Random Forest (`max_depth=5`)
* **Strengths**: Combines multiple decorrelated trees and limits depth, reducing the overfitting seen in a single unconstrained tree.
* **Weaknesses**: Less directly interpretable than a single tree or linear model, and slower to train on very large datasets.

### C. Logistic Regression (with `StandardScaler` + L2 Regularization)
* **Strengths**: Delivers the highest test accuracy (**~98.2%**) and F1-Score (**~0.986**) with minimal train-test gap, proving strong generalization. Fast to train and outputs calibrated probabilities.
* **Weaknesses**: Requires feature scaling (`StandardScaler`) and assumes roughly linear class boundaries.

---

## 4. Conclusion
Limiting tree depth and using ensemble bagging improved tree test accuracy from **~91.2% to ~95.6%**, while pairing **feature scaling** with **L2-regularized Logistic Regression** achieved the strongest, most balanced performance (**~98.2% test accuracy**).
