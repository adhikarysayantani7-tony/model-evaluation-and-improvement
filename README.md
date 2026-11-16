# Model Evaluation & Performance Improvement

## Project Overview
This repository evaluates and compares multiple supervised classification models on Scikit-Learn's Breast Cancer Wisconsin dataset, diagnosing underfitting and overfitting while demonstrating performance improvement through regularization and feature scaling.

## Repository Structure
- `README.md`: Project overview, comparison table, and usage guide
- `requirements.txt`: Required Python dependencies
- `notebooks/model_evaluation_and_improvement.ipynb`: Interactive Jupyter Notebook with evaluation metrics, train vs. test charts, and confusion matrix
- `docs/evaluation_report.md`: Short report explaining metric selection and model strengths & weaknesses

## Performance Comparison Table

| Model Configuration | Train Accuracy | Test Accuracy | Precision | Recall | F1-Score | Diagnosis |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Decision Tree (`max_depth=1`)** | ~92.3% | ~89.5% | ~90.1% | ~93.1% | ~0.916 | Underfitting (High Bias) |
| **Decision Tree (`max_depth=None`)** | 100.0% | ~91.2% | ~95.6% | ~90.3% | ~0.929 | Overfitting (High Variance) |
| **Random Forest (`max_depth=5`)** | ~99.3% | ~95.6% | ~95.9% | ~97.2% | ~0.966 | Improved Ensemble |
| **Logistic Regression (Scaled + L2)** | ~98.9% | **~98.2%** | **~98.6%** | **~98.6%** | **~0.986** | Best Generalization |

## Key Takeaways
* **Overfitting vs. Underfitting**: Limiting Decision Tree depth and using Random Forest bagging reduced overfitting and boosted test accuracy from ~91.2% to ~95.6%.
* **Best Model**: Pairing `StandardScaler` with L2-regularized Logistic Regression achieved ~98.2% test accuracy and 0.986 F1-score.
* **Detailed Analysis**: See `docs/evaluation_report.md` for metric selection rationale and model strengths & weaknesses.

## How to Run
1. Clone the repository:
   `git clone https://github.com/adhikarysayantani7-tony/model-evaluation-and-improvement.git`
2. Install dependencies:
   `pip install -r requirements.txt`
3. Open the notebook:
   `jupyter notebook notebooks/model_evaluation_and_improvement.ipynb`
