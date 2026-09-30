# Model justification

Logistic Regression was selected because it achieved the highest mean five-fold cross-validation F1 for approved loans (0.8714) using the training data only. On the held-out set, it achieved 86.18% accuracy, 84.00% precision, 98.82% recall, an F1-score of 0.9081, and ROC-AUC of 0.8517. Its confusion matrix shows 106 correct predictions, with false-approval and false-rejection counts of 16 and 1, respectively, supporting the choice under this F1 objective while showing that some approval errors remain.
