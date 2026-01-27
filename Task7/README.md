# Task 7: Titanic Survival Prediction - Evaluation & Analysis Report

## 📋 Project Overview

This project demonstrates a complete machine learning pipeline for binary classification using the Titanic dataset. The objective is to predict passenger survival based on various demographic and travel-related features.

---

## 📊 Dataset Description

- **Source**: Seaborn's built-in Titanic dataset
- **Total Samples**: 891 passengers
- **Target Variable**: `survived` (0 = Did not survive, 1 = Survived)
- **Survival Rate**: ~38.4% (imbalanced dataset)

### Original Features

| Feature | Type | Description |
|---------|------|-------------|
| `survived` | int64 | Target variable (0/1) |
| `pclass` | int64 | Passenger class (1, 2, 3) |
| `sex` | object | Gender (male/female) |
| `age` | float64 | Age in years |
| `sibsp` | int64 | Number of siblings/spouses aboard |
| `parch` | int64 | Number of parents/children aboard |
| `fare` | float64 | Ticket fare |
| `embarked` | object | Port of embarkation (C/Q/S) |
| `class` | category | Passenger class (First/Second/Third) |
| `who` | object | Person type (man/woman/child) |
| `adult_male` | bool | Adult male indicator |
| `deck` | category | Deck location |
| `embark_town` | object | Embarkation town name |
| `alive` | object | Survival status (yes/no) |
| `alone` | bool | Traveling alone indicator |

---

## 🔧 Data Preprocessing Steps

### 1. Missing Value Analysis

| Column | Missing Values | Percentage |
|--------|----------------|------------|
| `age` | 177 | 19.9% |
| `deck` | 688 | 77.2% |
| `embarked` | 2 | 0.2% |
| `embark_town` | 2 | 0.2% |

### 2. Feature Removal

The following columns were dropped due to high missing values or redundancy:
- `deck` - 77.2% missing values
- `alive` - Redundant with target variable `survived`
- `embarked` - Redundant with `embark_town`
- `class` - Redundant with `pclass`

### 3. Missing Value Imputation

| Column | Imputation Strategy | Value Used |
|--------|---------------------|------------|
| `age` | Median imputation | 28.0 years |
| `embark_town` | Mode imputation | Southampton |

### 4. Categorical Encoding

**One-Hot Encoding** (with `drop_first=True`) was applied to:
- `sex` → `sex_male`
- `who` → `who_man`, `who_woman`
- `embark_town` → `embark_town_Queenstown`, `embark_town_Southampton`

### 5. Final Feature Set (12 features)

After preprocessing, the following features were used for modeling:

| Feature | Type |
|---------|------|
| `pclass` | int64 |
| `age` | float64 |
| `sibsp` | int64 |
| `parch` | int64 |
| `fare` | float64 |
| `adult_male` | bool |
| `alone` | bool |
| `sex_male` | bool |
| `who_man` | bool |
| `who_woman` | bool |
| `embark_town_Queenstown` | bool |
| `embark_town_Southampton` | bool |

### 6. Train-Test Split

- **Training Set**: 80% (712 samples)
- **Test Set**: 20% (179 samples)
- **Random State**: 42

### 7. Feature Scaling

**StandardScaler** was applied to normalize all features to zero mean and unit variance.

---

## 🤖 Model: Logistic Regression

**Algorithm**: Logistic Regression (scikit-learn default parameters)

Logistic Regression was chosen for this binary classification task due to its:
- Interpretability
- Efficiency with smaller datasets
- Good baseline performance for binary classification

---

## 📈 Model Performance

### Accuracy Score

| Metric | Value |
|--------|-------|
| **Accuracy** | **81.56%** |

### Confusion Matrix

|  | Predicted: 0 | Predicted: 1 |
|--|--------------|--------------|
| **Actual: 0** | 91 (TN) | 14 (FP) |
| **Actual: 1** | 19 (FN) | 55 (TP) |

### Classification Report

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| **0 (Not Survived)** | 0.83 | 0.87 | 0.85 | 105 |
| **1 (Survived)** | 0.80 | 0.74 | 0.77 | 74 |
| **Macro Avg** | 0.81 | 0.80 | 0.81 | 179 |
| **Weighted Avg** | 0.81 | 0.82 | 0.81 | 179 |

### Performance Metrics Summary

| Metric | Value |
|--------|-------|
| Overall Accuracy | 81.56% |
| Precision (Survived) | 80% |
| Recall (Survived) | 74% |
| F1-Score (Survived) | 77% |
| ROC-AUC Score | ~0.85 |

---

## 📉 Visualizations

The notebook includes the following visualizations:

1. **Confusion Matrix Heatmap** - Visual representation of model predictions vs actual values
2. **ROC Curve** - Shows the trade-off between True Positive Rate and False Positive Rate with AUC score

---

## 🔍 Key Insights

### Model Strengths
- High overall accuracy (81.56%)
- Good precision for both classes (83% for non-survivors, 80% for survivors)
- Reasonable F1-scores indicating balanced performance

### Areas for Improvement
- Recall for survivors (74%) is lower than for non-survivors (87%)
- 19 passengers who survived were incorrectly predicted as not surviving (false negatives)

---

## 🛠️ Technologies Used

- **Python** 3.12
- **NumPy** - Numerical computing
- **Pandas** - Data manipulation
- **Matplotlib & Seaborn** - Visualization
- **Scikit-learn** - Machine learning pipeline
  - `train_test_split` - Data splitting
  - `StandardScaler` - Feature scaling
  - `LogisticRegression` - Classification model
  - `accuracy_score`, `confusion_matrix`, `classification_report` - Evaluation metrics
  - `roc_auc_score`, `roc_curve` - ROC analysis

---

## 📁 File Structure

```
Task7/
├── preprocessing.ipynb   # Main notebook with EDA, preprocessing, and modeling
└── README.md             # This evaluation report
```

---

## 🚀 How to Run

1. Open `preprocessing.ipynb` in Jupyter Notebook or Google Colab
2. Run all cells sequentially
3. The notebook will:
   - Load the Titanic dataset
   - Perform data preprocessing
   - Train the Logistic Regression model
   - Display evaluation metrics and visualizations

---

## 📝 Conclusion

The Logistic Regression model achieves a solid baseline performance with **81.56% accuracy** on the Titanic survival prediction task. The preprocessing pipeline effectively handles missing values, encodes categorical variables, and scales features for optimal model performance. The model shows balanced precision across both classes with a ROC-AUC score of approximately 0.85, indicating good discriminative ability between survivors and non-survivors.
