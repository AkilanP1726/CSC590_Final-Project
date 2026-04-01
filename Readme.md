Genomics SNP Binary Classification - Machine Learning Pipeline

A Research Project for CSC 590 - California State University, Dominguez Hills

Project Overview

This project builds a complete machine learning pipeline for predicting a binary phenotype from simulated genomic SNP datasets. Each dataset represents different genetic interaction types:

4-way Additive

2-way Epistasis

Additive + Epistatic Mix

Heterogeneous Genetic Architectures

The project follows real genomic simulation designs used in GAMETES and related research (Urbanowicz et al., 2012; Woodward et al., 2022).
The goal is to analyze how ML models behave under additive, epistatic, and heterogeneous genetic effects - and to build a reproducible evaluation framework.

Dataset Categories
1. Basic Datasets (100 features)

Fully functional and used for training/testing.

Dataset	Description	Status
4-wayAdditive_100feat.txt	Pure additive SNP effects	Modeled
2Additive_2-wayEpi_100feat.txt	Additive + epistasis	Modeled
2-wayEpi_100feat.txt	Pure 2-locus epistasis	Modeled
4-wayHeterogeneous_100feat.txt	Mixed genetic architecture	Modeled
2. Challenge Datasets (10,000 features)

These load successfully but all rows contain only NA, including the label column.

Dataset	Issue	Status
4-wayAdditive_10000feat_with_NA.txt	100% missing	Excluded
2Additive_2-wayEpi_10000feat_with_NA.txt	100% missing	Excluded
2-wayEpi_10000feat_with_NA.txt	100% missing	Excluded
4-wayHeterogeneous_10000feat_with_NA.txt	100% missing	Excluded

A complete discussion of these errors is included in the report.

Machine Learning Models Used

The pipeline trains & evaluates:

Logistic Regression

Random Forest

Gradient Boosting Machines (GBM)

Support Vector Machines (SVM)

Each model uses:

5-fold Stratified Cross-Validation

ROC-AUC scoring

Hyperparameter tuning

Balanced class weights

Pipeline Features
Automatic Dataset Loader

Attempts multiple parsing strategies and validates the label column.

Missing Value Handling

Median imputation for SNP features

Removal of invalid label rows

Trained Model Artifacts

For each dataset/model, the pipeline saves:

confusion_matrix.png
roc_curve.png
pr_curve.png
feat_importance_top20.png
classification_report.txt
cv_results.csv
model.joblib
summary.csv

Global Summary

A combined summary_all.csv ranks all models across all datasets.

Tools & Libraries
Component	Description
Python 3.10	Main programming language
Pandas / NumPy	Data loading, preprocessing
Scikit-Learn	Modeling, CV, metrics
Matplotlib	Plotting outputs
Joblib	Saving trained models
Jupyter Notebook	Experimentation environment
Installation
1. Clone or download the project
git clone https://github.com/<your-username>/genomics-snp-ml.git
cd genomics-snp-ml

2. Install dependencies
pip install -r requirements.txt


or manually:

pip install numpy pandas scikit-learn matplotlib joblib

Running the Pipeline

Place your datasets under:

data/basic/
data/challenge/


Open the script:

DATA_ROOT = Path(r"C:\Users\apandiyan1\Documents\Academics\Fall 2025\CSC 590 - Final Project\Simulated_Genomic_Binary-Class\data")


Run:

python pipeline.py

Key Results Summary
Dataset	Best Model	ROC-AUC	Notes
4-way Additive	Logistic Regression	~0.996	Strong linear signal
2-Additive/Epistasis	Gradient Boosting	~0.706	Moderate difficulty
2-way Epistasis	Random Forest	~0.510	Very challenging
Heterogeneous	Gradient Boosting	~0.716	Mixed feature importance
Why epistasis is hard?

Traditional ML models assume additive patterns. Epistasis requires learning interacting non-linear feature combinations, which is more complex.

Insert-Ready Figure Captions (for Report Appendix)
ROC Curves

“ROC curve showing the trade-off between true-positive and false-positive rates across classification thresholds for each model. Additive datasets show strong separability, while epistatic datasets show weaker discriminability.”

Precision–Recall Curves

“PR curve illustrating model performance under class imbalance. Additive datasets maintain high precision across recall levels.”

Confusion Matrices

“Confusion matrix visualizing correct/incorrect predictions. Additive datasets show strong diagonal dominance, while epistatic datasets contain more off-diagonal misclassifications.”

Feature Importance

“Top-20 SNP features ranked by model-based importance. Additive datasets reveal expected causal SNPs, matching the ground-truth architecture.”

References

• Urbanowicz, R.J., Kiralis, J., Sinnot-Armstrong, N.A., Heberling, T., Fisher, J.M. and Moore, J.H., 2012. GAMETES: a fast, direct algorithm for genera􀆟ng pure, strict, epista􀆟c models with random architectures. BioData mining, 5, pp.1-14.
• Urbanowicz, R.J., Kiralis, J., Fisher, J.M. and Moore, J.H., 2012. Predic􀆟ng the difficulty of pure, strict, epista􀆟c models: metrics for simulated model selec􀆟on. BioData mining, 5(1), pp.1-13.
• Woodward, A.A., Urbanowicz, R.J., Naj, A.C. and Moore, J.H., 2022. Gene􀆟c heterogeneity: Challenges, impacts, and methods through an associa􀆟ve lens. Genetic Epidemiology, 46(8), pp.555-571.
• Urbanowicz, R.J., Meeker, M., La Cava, W., Olson, R.S. and Moore, J.H., 2018. Relief-based feature selec􀆟on: Introduc􀆟on and review. Journal of biomedical informatics, 85, pp.189-203.
• Urbanowicz, R.J., Olson, R.S., Schmit, P., Meeker, M. and Moore, J.H., 2018. Benchmarking relief-based feature selec􀆟on methods for bioinforma􀆟cs data mining. Journal of biomedical informatics, 85, pp.168-188.
• Urbanowicz, R., Zhang, R., Cui, Y. and Suri, P., 2023. STREAMLINE: A Simple, Transparent, End-To-End Automated Machine Learning Pipeline Facilita􀆟ng Data Analysis and Algorithm Comparison. In Gene􀆟c Programming

Author

Akilan Pandiyan
Master of Science in Computer Science
California State University, Dominguez Hills

Supervisor: Dr. Hooshmand

License

This project is for academic and research use only.