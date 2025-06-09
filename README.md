# Breast-cancer-ml
Introduction
Breast cancer is a leading cause of mortality among women worldwide. Early and accurate diagnosis is crucial for improving patient outcomes. Machine learning techniques can assist clinicians by analyzing quantitative measurements of cell nuclei from digitized images of fine-needle aspirate biopsies. This study leverages the Wisconsin Breast Cancer Diagnostic dataset, applying a full pipeline of preprocessing, exploratory analysis, unsupervised learning, and supervised classification to distinguish benign from malignant tumors.

Data Description & Preprocessing
Dataset: 571 samples × 32 columns
id: unique sample identifier
diagnosis: target variable (M = malignant, B = benign)
30 numeric features: ten measurement types (radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension), each reported as mean, standard error, and “worst” values.
