# 📊 Exploratory Data Analysis (EDA) Report

This repository contains basic exploratory data analysis performed on two datasets:

1. **Titanic Dataset**
2. **Students Performance Dataset**

The goal of this analysis is to understand the structure, quality, and machine learning suitability of the datasets before model building.

## 1. Loading and Inspecting the Dataset

Both datasets were loaded using **Pandas**.
The first few (`head()`) and last few (`tail()`) records were displayed to:

* Understand the overall structure
* Identify column names
* Get a sense of data types and values
* Check for obvious inconsistencies

This step helped in forming an initial intuition about the data.

---

## 2. Feature Type Identification (Manual Inspection)

Based on column names and values, features were manually categorized as follows:

### 🚢 Titanic Dataset

* **Numerical Features**: `Age`, `Fare`, `SibSp`, `Parch`
* **Categorical Features**: `Sex`, `Embarked`, `Cabin`, `Ticket`
* **Ordinal Features**: `Pclass` (1st, 2nd, 3rd class)
* **Binary Features**: `Survived` (Target), `Sex` (after encoding)

### 🎓 Students Performance Dataset

* **Numerical Features**: `Age`, `Gender`, `Ethnicity`, `ParentalEducation`, `StudyTimeWeekly`, `Absences`, `Tutoring`, `ParentalSupport`, `Extracurricular`, `Sports`, `Music`, `Volunteering`, `GPA`, `GradeClass`

This classification helps in choosing appropriate preprocessing techniques.

---

## 3. Dataset Structure and Statistics

The following Pandas functions were used:

* `df.info()` → to check:

  * Data types
  * Non-null counts
  * Missing values
* `df.describe()` → to analyze:

  * Mean, median, standard deviation
  * Min/max values
  * Distribution spread

### Observations:

* Titanic dataset contains **missing values**, especially in `Age`, `Cabin`, and `Embarked`.
* Students Performance dataset is **clean**, with no major missing values.

---

## 4. Unique Value Analysis (Categorical Columns)

Unique values in categorical columns were checked using `unique()` to:

* Understand category distribution
* Identify rare or dominant categories
* Detect possible imbalance

### Key Insights:

* Titanic has **imbalanced categories** in `Survived` and `Sex`.
* Students dataset shows **balanced gender distribution**, but some imbalance in parental education levels.

---

## 5. Target Variable and Input Features

### 🎯 Titanic Dataset

* **Target Variable**: `Survived`
* **Input Features**: Passenger demographics and travel-related attributes

### 🎯 Students Performance Dataset

* **Target Variable**: `GradeClass` (classification), `GPA` (regression)
* **Input Features**: Demographic and academic background information

Both datasets are suitable for supervised machine learning tasks.

---

## 6. Dataset Size and ML Suitability

| Dataset              | Records    | Suitability                            |
| -------------------- | ---------- | -------------------------------------- |
| Titanic              | ~891 rows  | Suitable for ML (small-medium dataset) |
| Students Performance | ~2300 rows | Suitable for ML and EDA                |

Both datasets are manageable in size and ideal for learning and experimentation.

---

## 7. Data Quality Observations

### 🚢 Titanic Dataset

* Missing values in key columns (`Age`, `Cabin`)
* Class imbalance in target variable (`Survived`)
* Requires preprocessing:

  * Missing value imputation
  * Encoding categorical variables
  * Feature selection

### 🎓 Students Performance Dataset

* Clean dataset with minimal data quality issues
* No missing values
* Suitable for direct modeling after scaling

---

## ✅ Conclusion

* Both datasets are **well-suited for machine learning**.
* Titanic requires **careful preprocessing**, while Students Performance is relatively **clean and ready**.
* The EDA provides a strong foundation for feature engineering and model development.

---