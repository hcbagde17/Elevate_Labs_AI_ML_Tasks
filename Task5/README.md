# Heart Disease Classification - Model Evaluation Report

## Project Overview

This project implements a **Logistic Regression** model to predict heart disease using the UCI Heart Disease dataset. The analysis includes comprehensive data exploration, preprocessing, and model evaluation.

---

## Dataset Information

| Attribute | Description |
|-----------|-------------|
| **Samples** | 303 patients |
| **Features** | 13 clinical attributes |
| **Target** | Binary classification (0 = No heart disease, 1 = Heart disease) |
| **Missing Values** | None |

### Features

| Feature | Type | Description |
|---------|------|-------------|
| `age` | Numeric | Patient age in years |
| `sex` | Binary | 1 = Male, 0 = Female |
| `cp` | Categorical (0-3) | Chest pain type |
| `trestbps` | Numeric | Resting blood pressure (mm Hg) |
| `chol` | Numeric | Serum cholesterol (mg/dl) |
| `fbs` | Binary | Fasting blood sugar > 120 mg/dl |
| `restecg` | Categorical (0-2) | Resting ECG results |
| `thalach` | Numeric | Maximum heart rate achieved |
| `exang` | Binary | Exercise-induced angina |
| `oldpeak` | Numeric | ST depression induced by exercise |
| `slope` | Categorical (0-2) | Slope of peak exercise ST segment |
| `ca` | Categorical (0-4) | Number of major vessels colored by fluoroscopy |
| `thal` | Categorical (0-3) | Thalassemia type |

---

## Preprocessing Steps

### 1. Data Loading and Initial Inspection
- Loaded the dataset from `heart.csv`
- Verified data structure using `df.info()` and `df.head()`

### 2. Missing Value Analysis
```
All features: 0 missing values
```
The dataset is complete with no null values in any column.

### 3. Exploratory Data Analysis (EDA)
- **Target Distribution Analysis**: Examined the balance between heart disease positive and negative cases
- **Feature Distributions**: Visualized distributions using histograms with KDE for continuous variables (age, trestbps, chol, thalach, oldpeak)
- **Statistical Summary**: Generated descriptive statistics for all features

### 4. Feature Scaling
- **Method**: StandardScaler
- **Purpose**: Normalize feature scales to improve Logistic Regression convergence
- **Application**: Applied to all numerical features

### 5. Train-Test Split
- **Split Ratio**: 80% training, 20% testing
- **Training Samples**: 242
- **Testing Samples**: 61

---

## Model Training

### Algorithm: Logistic Regression

**Configuration:**
| Parameter | Value |
|-----------|-------|
| Penalty | L2 (Ridge) |
| Solver | lbfgs |
| Max Iterations | 100 |
| Regularization (C) | 1.0 |

---

## Model Performance Results

### Accuracy Score
```
Accuracy: 85.25%
```

### Confusion Matrix
|                    | Predicted: No Disease | Predicted: Disease |
|--------------------|----------------------|-------------------|
| **Actual: No Disease** | 25 (TN) | 4 (FP) |
| **Actual: Disease**    | 5 (FN)  | 27 (TP) |

### Classification Report

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| **0 (No Disease)** | 0.83 | 0.86 | 0.85 | 29 |
| **1 (Disease)** | 0.87 | 0.84 | 0.86 | 32 |
| **Accuracy** |  |  | 0.85 | 61 |
| **Macro Avg** | 0.85 | 0.85 | 0.85 | 61 |
| **Weighted Avg** | 0.85 | 0.85 | 0.85 | 61 |

---

## Key Metrics Interpretation

### Precision
- **Class 0 (No Disease)**: 83% - When the model predicts no heart disease, it's correct 83% of the time
- **Class 1 (Disease)**: 87% - When the model predicts heart disease, it's correct 87% of the time

### Recall
- **Class 0 (No Disease)**: 86% - The model correctly identifies 86% of patients without heart disease
- **Class 1 (Disease)**: 84% - The model correctly identifies 84% of patients with heart disease

### F1-Score
- Balanced harmonic mean of precision and recall
- Both classes achieve approximately 0.85-0.86, indicating consistent performance

---

## Conclusions

1. **Strong Performance**: The Logistic Regression model achieves 85.25% accuracy, demonstrating effective classification capability on this dataset.

2. **Balanced Classification**: Similar performance metrics across both classes indicate the model handles the classification task without significant bias.

3. **Low Error Rate**: Only 9 misclassifications out of 61 test samples (4 false positives, 5 false negatives).

4. **Clinical Relevance**: The false negative rate (5 patients with disease predicted as healthy) is a key concern for medical applications and may require threshold adjustment for real-world deployment.

---

## Files in This Project

- `heart.csv` - Raw dataset
- `eda&preprocess.ipynb` - Jupyter notebook with EDA, preprocessing, and model training
- `README.md` - This evaluation report

---

## Requirements

```
numpy
pandas
matplotlib
seaborn
scikit-learn
```

---