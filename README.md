# Breast-cancer-ml
This study applies a full machine-learning pipeline to the Wisconsin Breast Cancer Diagnostic dataset (571 samples, 32 attributes), moving from data cleaning and exploratory analysis through unsupervised learning, supervised classification, and rigorous evaluation. Median imputation resolved missing values, duplicate entries were removed, and the binary diagnosis label was encoded. Principal Component Analysis (PCA) showed that the first three components capture 48.6 %, 12.7 %, and 5.3 % of variance, respectively. K-Means clustering on the two-component projection yielded a Silhouette score of 0.50 and a Davies–Bouldin score of 0.70. Three classifiers—Logistic Regression, Support Vector Machine (SVM), and Random Forest—were trained on an 80/20 split. Logistic Regression performed best on the hold-out set with 97.4 % accuracy, while all models achieved ROC AUC ≥ 0.98 and average precision ≥ 0.96. Random Forest feature importances highlighted nuclear area and concavity measures as the strongest predictors.

After dropping the id column, median imputation filled all remaining missing values and four duplicate samples were removed, leaving 566 unique observations. The target distribution was:
| Diagnosis     | Count |
| ------------- | ----- |
| Benign (0)    | 356   |
| Malignant (1) | 210   |

Histograms and boxplots revealed that malignant tumors tend to have larger mean radii and areas. A correlation heatmap (annotated to two decimals) exposed very strong linear relationships among size features.

PCA reduced the 30-dimensional feature space for visualization and clustering:
| Principal Component | Explained Variance Ratio |
| ------------------- | ------------------------ |
| PC1                 | 0.4862                   |
| PC2                 | 0.1270                   |
| PC3                 | 0.0529                   |

Applying K-Means (k=2) to the two-component data produced:
| Metric               | Score |
| -------------------- | ----- |
| Silhouette Score     | 0.51  |
| Davies–Bouldin Score | 0.83  |

Features were standardized and the data split 80/20. The following metrics were obtained on the test set:
| Model               | Accuracy | Precision | Recall | F1-Score |
| ------------------- | -------: | --------: | -----: | -------: |
| Logistic Regression |   0.9737 |    0.9583 | 0.9787 |   0.9684 |
| SVM (RBF kernel)    |   0.9649 |    0.9574 | 0.9574 |   0.9574 |
| Random Forest       |   0.9474 |    0.9362 | 0.9362 |   0.9362 |

All three models achieved ROC AUC ≥ 0.98 and average precision (area under the PR curve) ≥ 0.96:
| Model               | ROC AUC | Avg. Precision |
| ------------------- | ------: | -------------: |
| Logistic Regression |    0.99 |           0.97 |
| SVM (RBF kernel)    |    0.99 |           0.96 |
| Random Forest       |    0.98 |           0.96 |

This analysis demonstrates that simple, well-tuned models can achieve high accuracy (≈ 97 %) in distinguishing benign from malignant tumors using nuclear measurements alone. Key predictors include extreme (“worst”) measurements of area and concavity. Before clinical deployment, models require validation on diverse, external cohorts to guard against sampling bias. Patient confidentiality and informed consent must be maintained when handling such data. Ultimately, while these tools can enhance diagnostic workflows, they should serve to augment rather than replace expert clinical judgment.

