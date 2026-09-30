# Steps to run, publish and submit the loan classification assignment

## 1. Download and extract
Download `Loan_Classification_Project.zip`. On Windows, right-click the ZIP and choose Extract All. Open the `loan-classification` folder. You will see the notebook, README, requirements file, guide, data folder and outputs folder.

## 2. Run on Kaggle and get your notebook link
1. Sign in at https://www.kaggle.com/.
2. Open https://www.kaggle.com/datasets/altruistdelhite04/loan-prediction-problem-dataset and click New Notebook.
3. In the notebook editor, choose File > Import Notebook (or Upload Notebook) and select `Loan_Classification_Models.ipynb`.
4. Set the title to `Loan Prediction - Classification Model Comparison`.
5. Check the Input/Data panel. If the dataset is missing, click Add Input/Add Data, search `altruistdelhite04/loan-prediction-problem-dataset`, and attach it.
6. Confirm the dataset contains `train_u6lujuX_CVtuZ9i.csv` and `test_Y3wMUE5_7gLdaTN.csv`. The notebook locates them automatically.
7. Choose Run All. Keep CPU enabled; no GPU is required. Cross-validation fits several candidate models, so allow a few minutes.
8. Check that all cells finish successfully. Look for the metrics comparison, confusion matrix, ROC curves and three-sentence justification.
9. Click Save Version and choose Save & Run All, or the equivalent run-and-save option. Wait until the saved version finishes.
10. Use Share/visibility settings to make the notebook Public if your teacher requires public access. Open the saved notebook page and copy its actual URL.
11. Test the link in an incognito window. A notebook URL normally looks like `https://www.kaggle.com/code/YOUR_USERNAME/YOUR_NOTEBOOK_SLUG`; do not submit this placeholder.

Menu wording can vary. Kaggle documentation: https://www.kaggle.com/docs/notebooks

## 3. Create your GitHub repository link
1. Sign in to GitHub and open https://github.com/new.
2. Name the repository `loan-classification` and add a description such as `Loan status prediction using Logistic Regression, Decision Tree and Random Forest`.
3. Select Public if your teacher needs public access, add a starter README, and click Create repository.
4. Choose Add file > Upload files. Drag the CONTENTS of the extracted project folder into the upload area, including the data and outputs folders. Upload the extracted contents, not only the ZIP.
5. Include the supplied README.md, which replaces the starter README. Add a commit message such as `Add completed loan classification assignment` and confirm the commit. If a branch/pull-request flow is shown, finish and merge it to put the files on the default branch.
6. Open `Loan_Classification_Models.ipynb` on GitHub and confirm the saved tables and plots are visible. GitHub previews the saved output; it does not run the notebook.
7. Copy the repository URL, normally shaped like `https://github.com/YOUR_USERNAME/loan-classification`.
8. Edit README.md to include your real Kaggle notebook link. You may also add the GitHub link to the first Markdown cell in your Kaggle notebook and save another version.
9. Verify both public links in an incognito window. If your teacher requests private repositories, follow their access instructions instead.

GitHub documentation:
- https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository
- https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository

## 4. Optional: run on Google Colab
1. Open https://colab.research.google.com/ and select Upload notebook.
2. Upload `Loan_Classification_Models.ipynb`.
3. Open the left Files sidebar and upload both CSVs from the extracted data folder.
4. Choose Runtime > Run all. The notebook also checks `/content/` for the files.
5. Review the results and download the executed notebook if required. A Colab runtime reset removes uploaded files, so upload the CSVs again when needed.

## 5. Submit these items
- The executed `.ipynb` notebook, if the submission portal requests a file.
- Your own Kaggle notebook link.
- Your GitHub repository link.
- The dataset source URL as attribution.
- The comparison table and confusion matrix are included in the notebook and saved separately under outputs/.
- The 2–3 sentence justification is in the notebook and `outputs/model_justification.md`.

The dataset URL is not your completed notebook URL. Your personal Kaggle/GitHub links are created when you publish under your accounts; no personal publication links have been created here.

## What the code does
1. Loads labeled and unlabeled source files and checks missingness, duplicates and IDs.
2. Separates Loan_Status from predictors and reserves a stratified test set.
3. Fits imputation, encoding and scaling only on training data within pipelines.
4. Trains/tunes Logistic Regression, Decision Tree and Random Forest using cross-validation.
5. Selects by training CV F1 and reports final held-out Accuracy, Precision, Recall, F1 and ROC-AUC.
6. Shows the selected model's confusion matrix and class-specific report.
7. Saves the results and optionally predicts labels for the unlabeled source test file.

The optional prediction CSV is not necessary for the assignment and has no measured accuracy, because those 367 records do not include true labels. There is no competition submission step required by this dataset-page assignment.
