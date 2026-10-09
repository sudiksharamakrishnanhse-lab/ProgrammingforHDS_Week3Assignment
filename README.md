# ProgrammingforHDS_Week3Assignment
Automated Analysis Pipeline Exploration Assignment

1. Purpose
This notebook demonstrates a structured and reproducible analysis workflow in a health data science setting. It uses the Pima Indians Diabetes Database, which contains diagnostic measurements from women aged 21 or older of Pima Indian heritage. The prediction task is to classify whether a patient has diabetes (Outcome = 1) or not (Outcome = 0) from predictors such as glucose, BMI, blood pressure, insulin, age, and pregnancies.

Four blocks were added to extend the provided pipeline.
- Automatic skewness check: Measures the skewness of every numeric variable and, if the skewness is beyond the cutoff, recommends the median; if not, recommends the mean
- Automatic scatterplots for the most correlated pairs:  predictor pairs by correlation and plots the strongest ones, colored by outcome. If no pair reaches the cutoff, prints a message and draws nothing; otherwise plots the top pairs
- Automated multicollinearity screening: Calculates a variance inflation factor for every predictor. Flags a predictor if its VIF is at or above vif_cutoff; reports whether any predictor was flagged
- Automatic baseline comparison: Compares model accuracy to the accuracy of always guessing the majority class. If the model beats the baseline, reports that it is learning from the predictors; otherwise says it is not

2. Instructions for Running Analysis
- Open the notebook
- Save your own copy: File > Save a copy in Drive.
- Get the dataset. Download the Pima Indians Diabetes dataset as a CSV or Excel file. The notebook expects one row per patient and these columns: Pregnancies, Glucose, D_BP, Skin_Thickness, Insulin, BMI, Pedigree, Age, and Outcome.
- Run the notebook from top to bottom. Use Runtime > Run all.
- Upload the file when prompted. The "Upload your dataset" cell opens an upload dialog. Upload the correct CSV file
- Review the outputs under each section, then read the written explanations beneath the automated blocks.

3. Google Collab Link - https://colab.research.google.com/drive/1wc8SGT0KjpfZ-NHzE3Dfm2vHUEcYNez6?usp=sharing

4. Required Software/Libraries
pandas: Data loading and manipulation
numpy: Numerical operations
matplotlib, seaborn: Plots and visualizations
scipy: Statistical tests
statsmodels: ANOVA
scikit-learn: Imputation, scaling, pipelines, models, cross-validation, VIF calculation, and evaluation metrics
phik: Phi-K correlation matrix
google.colab: File upload

5. Assumptions/Limitations

Assumptions
- Zero values are missing data. For Glucose, D_BP, Skin_Thickness, Insulin, and BMI, a value of 0 is biologically impossible, so the notebook treats zeros in these columns as missing. Pregnancies is not treated this way, since 0 is valid.
- Missing values are filled with the median. Median imputation is used inside the modeling pipelines, which assumes that median replacement does not badly distort the data.
- The target is binary and coded as 0 (no diabetes) and 1 (diabetes). The pipeline raises an error otherwise.
- Observations are independent. Statistical tests and models assume each row is a separate patient.
- Thresholds are judgment calls. Cutoffs such as the skewness cutoff of 1.0, the correlation cutoff of 0.30, and the VIF cutoff of 5 are common rules of thumb, not universal standards. Changing them can change the automated decisions.

Limitations
- Small, specific sample. The data are 768 women of Pima Indian heritage aged 21 or older, so findings may not generalize to other populations.
- Imputation affects results. Insulin and Skin_Thickness have a large share of missing values, and filling them with medians can understate real variation.
- Skewness is a rough guide. The skewness check only recommends a summary statistic; it does not change or transform the data.
- Association is not causation. Correlations, test results, and model coefficients describe relationships in this dataset, not causes.
