# Loan Status Classification

Author: Akshat Shah

Predict `Loan_Status` using Logistic Regression, Decision Tree and Random Forest. The positive class is **Approved (Y=1)**; the negative class is **Not approved (N=0)**.

## Data and evaluation
- Kaggle source: https://www.kaggle.com/datasets/altruistdelhite04/loan-prediction-problem-dataset
- Labeled data: 614 applications, 422 Y and 192 N, with no exact duplicate rows.
- Source test file: 367 applications with no target labels; it is not used for evaluation.
- Stratified 80/20 split with random_state=42: 491 training applications and 123 held-out applications.
- Five-fold stratified training-only CV selects settings and the best model by positive-class F1. Mean CV ROC-AUC breaks a tie between models.
- Numeric imputation/scaling and categorical imputation/one-hot encoding are inside each pipeline and fitted within training folds.
- Exclude Loan_ID and Loan_Status from predictors. Use a fixed probability threshold of 0.5, with ties assigned to class N.

## Test metrics
All precision, recall and binary F1 values refer to Y. Macro-F1 gives equal weight to both classes. Higher values are better.

| Model | Accuracy | Precision (Y) | Recall (Y) | F1 (Y) | Macro-F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|---:|
| Logistic Regression | 0.8618 | 0.8400 | 0.9882 | 0.9081 | 0.8147 | 0.8517 |
| Decision Tree | 0.8537 | 0.8317 | 0.9882 | 0.9032 | 0.8016 | 0.7633 |
| Random Forest | 0.8537 | 0.8317 | 0.9882 | 0.9032 | 0.8016 | 0.8341 |

## Selected model

Logistic Regression was selected because it achieved the highest mean five-fold cross-validation F1 for approved loans (0.8714) using the training data only. On the held-out set, it achieved 86.18% accuracy, 84.00% precision, 98.82% recall, an F1-score of 0.9081, and ROC-AUC of 0.8517. Its confusion matrix shows 106 correct predictions, with false-approval and false-rejection counts of 16 and 1, respectively, supporting the choice under this F1 objective while showing that some approval errors remain.

## Confusion matrix

| Actual / Predicted | N | Y |
|---|---:|---:|
| Actual N | 22 | 16 |
| Actual Y | 1 | 84 |

Rows are actual labels; columns are predictions. A false approval means predicted Y with actual label N; it does not establish repayment/default behavior.

## Run the notebook
Kaggle: import `Loan_Classification_Models.ipynb` and attach the source dataset. Colab: upload the notebook and both CSVs via the Files sidebar. Local Jupyter: keep this directory structure, then run:

```bash
python -m pip install -r requirements.txt
jupyter notebook Loan_Classification_Models.ipynb
```

Run all cells from top to bottom. The notebook contains saved outputs and can also be read without running it. CPU is sufficient; no GPU is needed.

## Files
- `Loan_Classification_Models.ipynb`: three trained models, evaluated results, four chart figures, explanations and three-sentence justification.
- `data/`: two unchanged source CSVs.
- `outputs/model_comparison.csv`: required metric comparison.
- `outputs/best_model_confusion_matrix.csv`: selected model's confusion matrix.
- `outputs/best_model_classification_report.csv`: precision/recall/F1 for both classes.
- `outputs/model_justification.md`: required three-sentence justification.
- `outputs/charts/`: class distribution, model comparison, selected confusion matrix and ROC curves.
- `outputs/cross_validation_results.csv` and model CV search files: tuning details.
- `outputs/split_manifest.csv` and `outputs/holdout_predictions.csv`: reproducible split and evaluated predictions.
- `outputs/unlabeled_loan_predictions.csv`: optional predictions for the 367 unlabeled applications, from a separate final refit on all labeled data.
- `LOAN_SUBMISSION_GUIDE.md`: running, publishing and submitting instructions.

## Scope
The test set is small, so minor metric differences are not proof of universal superiority. Accuracy alone is insufficient because Y is the majority class; the notebook includes an always-approve baseline, macro-F1 and a class-specific report. Model selection uses training CV, while test results provide the final check. The dataset contains historical demographic attributes, and these classroom results do not establish fairness or real-world lending suitability.

Source credit: Kaggle uploader `altruistdelhite04`; original data are retained unchanged. This project does not claim ownership of the source dataset or assign it a new license.
