# Breast-cancer-ml
Introduction
Breast cancer is a leading cause of mortality among women worldwide. Early and accurate diagnosis is crucial for improving patient outcomes. Machine learning techniques can assist clinicians by analyzing quantitative measurements of cell nuclei from digitized images of fine-needle aspirate biopsies. This study leverages the Wisconsin Breast Cancer Diagnostic dataset, applying a full pipeline of preprocessing, exploratory analysis, unsupervised learning, and supervised classification to distinguish benign from malignant tumors.

Data Description & Preprocessing
Dataset: 571 samples × 32 columns

id: unique sample identifier

diagnosis: target variable (M = malignant, B = benign)

30 numeric features: ten measurement types (radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension), each reported as mean, standard error, and “worst” values.

Missing Values & Duplicates
Missing: up to 21 missing entries in some features

Imputation: median imputation for all numeric columns

Duplicates: 4 duplicate rows removed

Encoding & Data Types
Mapped diagnosis → {M:1, B:0} and converted to integer

Ensured no missing labels remained

Outlier Capping
IQR method applied to all numeric features: values outside [Q1–1.5·IQR, Q3+1.5·IQR] were capped to the bounds, reducing the impact of extreme measurements.

Exploratory Data Analysis
4.1 Class Distribution
Benign: 356 samples (63%)

Malignant: 212 samples (37%)

Slight class imbalance, manageable with standard classifiers.

4.2 Feature Distributions
Histograms and boxplots for radius_mean, texture_mean, and area_mean showed right-skewed distributions, with malignant tumors tending to have larger values.

4.3 Correlation Analysis
Correlation Heatmap (annotated to two decimals) identified many high correlations among size-related features.

Strong pairs (|r| ≥ 0.90):

radius_mean ↔ perimeter_mean (r ≈ 0.99)

area_mean ↔ radius_mean (r ≈ 0.98)

Several other mean–worst and se–se feature pairings.

 Unsupervised Learning
5.1 PCA
Reduced 30-dimensional feature space to 2 components for visualization:

PC1 explained ≈ 48% of variance

PC2 explained ≈ 12% of variance

A 3-component PCA captured over 65% of variance across PC1–PC3.

5.2 K-Means Clustering
Applied K-Means (k=2) on the 2-component PCA data.

Silhouette Score ≈ 0.50 indicated moderate cluster separation.

Davies-Bouldin Score ≈ 0.70 supported fair clustering structure.

Visualization showed partial separation of benign vs malignant groups in PC1–PC2 space.

6. Supervised Classification
6.1 Setup
Train/Test Split: 80% train / 20% test

Scaling: StandardScaler applied to all features

6.2 Models & Performance
| Model                  | Accuracy | Precision | Recall | F1-score |
| ---------------------- | -------: | --------: | -----: | -------: |
| Logistic Regression    |   0.9737 |    0.9583 | 0.9787 |   0.9684 |
| Support Vector Machine |   0.9649 |    0.9574 | 0.9574 |   0.9574 |
| Random Forest          |   0.9474 |    0.9362 | 0.9362 |   0.9362 |


Logistic Regression performed best overall.

Confusion Matrix for Logistic Regression showed few false positives/negatives.

6.3 ROC & Precision–Recall
All three classifiers achieved AUC ≥ 0.98 on ROC curves.

Average Precision (area under Precision–Recall) ≥ 0.96 for each model, indicating excellent discriminative ability even with class imbalance.

6.4 Feature Importances (Random Forest)
Top 5 most important features:

area_worst (importance ≈ 0.16)

concave_points_worst (≈ 0.15)

concave_points_mean (≈ 0.10)

radius_worst (≈ 0.09)

concavity_mean (≈ 0.07)

Conclusions & Recommendations
Primary Conclusion: Machine learning models can accurately distinguish benign vs malignant tumors using nuclear feature measurements—with Logistic Regression achieving ~97% accuracy.

Recommendations:

Validate models on external datasets to assess generalizability.

Explore ensemble methods or stacking for further performance gains.

Consider deep learning approaches on raw image data for end-to-end pipelines.

Ethical Considerations
Data Privacy: Ensure patient confidentiality when handling medical records.

Bias: Training data may not represent all demographics—models must be validated on diverse populations.

Human Oversight: ML tools should support, not replace, clinician judgment.
