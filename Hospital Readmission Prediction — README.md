# Hospital Readmission Prediction

A machine learning project for predicting whether a patient is likely to be readmitted to the hospital based on patient, diagnosis, treatment, and healthcare utilization information.

## Project Overview

Hospital readmission prediction can help identify patients who may require additional attention or follow-up after hospitalization. In this project, different machine learning classification algorithms were developed and compared to predict hospital readmission.

The project focuses on building a complete machine learning workflow, including data preprocessing, feature engineering, model comparison, hyperparameter tuning, feature importance analysis, classification threshold selection, and final evaluation on unseen test data.

## Objectives

- Explore and understand the hospital patient dataset
- Perform appropriate data preprocessing
- Create meaningful features from existing patient information
- Train and compare multiple classification models
- Tune the best-performing models using cross-validation
- Analyze important features contributing to model predictions
- Select an appropriate classification threshold based on validation performance
- Evaluate the final model on an unseen test set

## Machine Learning Workflow

The project follows these main steps:

1. Data Exploration
2. Feature Engineering
3. Train/Validation/Test Split
4. Numerical and Categorical Feature Separation
5. Missing Value Analysis
6. One-Hot Encoding
7. Feature Scaling
8. Model Training
9. Model Evaluation
10. Hyperparameter Tuning
11. Feature Importance Analysis
12. Classification Threshold Analysis
13. Final Test Set Evaluation

## Models Evaluated

The following classification algorithms were evaluated:

- Logistic Regression
- Random Forest
- XGBoost
- HistGradientBoosting
- Extra Trees
- K-Nearest Neighbors (KNN)

Hyperparameter tuning was performed for the selected tree-based models using `GridSearchCV` and cross-validation.

## Model Comparison

The tuned XGBoost model achieved the best validation performance among the evaluated models.

| Model | Validation ROC-AUC | Validation PR-AUC |
|---|---:|---:|
| Logistic Regression | 0.637 | 0.608 |
| Tuned Random Forest | 0.644 | 0.611 |
| **Tuned XGBoost** | **0.651** | **0.621** |
| HistGradientBoosting | 0.501 | 0.455 |
| Extra Trees | 0.503 | 0.463 |
| KNN | 0.509 | 0.469 |

## Best Model

The **tuned XGBoost classifier** was selected based on its validation performance.

### Validation Performance

- ROC-AUC: **0.651**
- PR-AUC: **0.621**

The tuned model showed substantially better generalization than the untuned XGBoost model, whose validation ROC-AUC was approximately 0.493 despite a training ROC-AUC of approximately 0.909.

## Feature Importance

Feature importance analysis was performed using the trained XGBoost model to identify features that contributed most to its predictions.

The most influential features included:

- `total_prior_visits`
- `n_inpatient`
- `diabetes_med`
- Medical specialty
- Glucose test results
- Age groups
- Diagnosis categories
- `procedures_per_day`
- `n_medications`
- `n_emergency`
- `inpatient_ratio`

The results suggest that previous healthcare utilization, patient characteristics, diagnoses, and treatment-related factors provide useful information for predicting hospital readmission.

Feature importance represents the features used most by the model for making predictions and should not be interpreted as evidence of causation.

## Classification Threshold

The default classification threshold of `0.50` was compared with several alternative thresholds using the validation set.

A threshold of **0.35** produced the highest validation F1-score among the tested thresholds and substantially increased recall compared with the default threshold.

The threshold was selected using the validation set and then kept fixed for the final test evaluation.

## Final Test Performance

The final tuned XGBoost model achieved:

- **ROC-AUC: 0.667**
- **PR-AUC: 0.646**

The model's threshold-based metrics were evaluated using the selected classification threshold of **0.35**.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Jupyter Notebook

## Key Concepts Demonstrated

This project demonstrates practical understanding of:

- Exploratory Data Analysis
- Feature Engineering
- Categorical Encoding
- Feature Scaling
- Classification
- Logistic Regression
- Tree-Based Models
- XGBoost
- Cross-Validation
- GridSearchCV
- Model Evaluation
- ROC-AUC
- PR-AUC
- Precision
- Recall
- F1-score
- Confusion Matrix
- Feature Importance
- Classification Threshold Optimization
- Prevention of Data Leakage through Pipelines

## Project Structure

```text
Hospital-Readmission-Prediction/
│
├── Hospital_Readmission_Prediction.ipynb
├── README.md
└── dataset/
    └── ...
```

> The dataset may not be included in the repository depending on its source and licensing restrictions.

## How to Run

1. Clone or download this repository.
2. Install the required Python libraries.
3. Open the Jupyter Notebook.
4. Run the notebook cells sequentially.

Example:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib jupyter
```

Then start Jupyter Notebook:

```bash
jupyter notebook
```

## Limitations

The model provides moderate predictive performance and should not be considered a clinical decision-making system. Further improvement would require additional relevant clinical information, larger and more representative datasets, model calibration, external validation, and evaluation in a real healthcare environment.

## Future Improvements

Potential improvements include:

- Additional feature engineering
- Model probability calibration
- More extensive hyperparameter optimization
- Explainability techniques such as SHAP
- External validation on a different dataset
- Evaluation using clinically motivated costs for false positives and false negatives
- Testing the model on more recent or diverse patient populations

## Conclusion

This project demonstrates an end-to-end machine learning approach to hospital readmission prediction. Multiple classification algorithms were compared, with tuned XGBoost providing the strongest validation performance. The final model achieved a test ROC-AUC of **0.667** and PR-AUC of **0.646**, providing a practical foundation for further experimentation and improvement in healthcare-focused machine learning.