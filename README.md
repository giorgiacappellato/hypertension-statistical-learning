# Statistical Learning for Hypertension Management

Statistical learning analysis of a hypertension intervention dataset using K-means clustering, SVM, GAM, and gradient boosting to predict and explain blood pressure reduction.

## Overview

This project explores a simulated dataset of 700 adult patients enrolled in a 6-month hypertension intervention program. The goal is to understand and predict the reduction in systolic blood pressure (SBP) using a combination of unsupervised and supervised statistical learning methods, and to identify which clinical, behavioral, and treatment-related factors drive treatment response.

## Dataset

- **n = 700** patients, 11 variables
- **Target (Y):** reduction in systolic blood pressure (mmHg) after 6 months
- **Predictors:**
  - *Clinical:* age, sex, baseline SBP, BMI, diabetes status
  - *Behavioral:* smoking status, exercise level, daily salt intake
  - *Treatment:* treatment arm (Control, Drug A, Drug B), therapy adherence

Data was split into training (70%) and test (30%) sets using a fixed random seed for reproducibility.

## Methods

| Method | Purpose |
|---|---|
| **K-means clustering** | Unsupervised patient segmentation based on continuous covariates; evaluated across k = 1–10 using within-cluster sum of squares and PCA visualization |
| **Support Vector Machine (radial kernel)** | Binary classification of "clinically successful" intervention (SBP reduction > 17 mmHg), with hyperparameter tuning (cost, gamma) and ROC/AUC evaluation |
| **Generalized Additive Model (GAM)** | Flexible non-linear modeling of SBP reduction using smoothing splines, with Bonferroni-corrected significance testing to isolate genuine non-linear effects |
| **Gradient Boosting (GBM)** | Tree-based ensemble model capturing multi-way covariate interactions, tuned across interaction depths (d = 1–7), with feature importance ranking |
| **Multiple Linear Regression** | Interpretable baseline for comparing predictive performance across all methods |

## Key Findings

- **K-means clustering** did not reveal well-separated patient subgroups — the cohort exists on a continuous clinical spectrum rather than discrete clusters.
- **Age and salt intake** are the dominant, strongly non-linear predictors of SBP reduction, consistently identified by both GAM and gradient boosting.
- **Baseline SBP and BMI** show significant, largely linear effects.
- **Treatment arm** matters: Drug A and Drug B outperform Control.
- **Gradient boosting (interaction depth = 3)** achieved the lowest test MSE among all models, outperforming GAM and linear regression by capturing non-linearities and interactions more effectively.

## How to Run the Project

Clone the repository:
   ```bash
   git clone https://github.com/<giorgiacappellato>/hypertension-statistical-learning.git
   ```

## License

This project is for educational purposes as part of a Statistical Learning course.
