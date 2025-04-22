
# System Threat Forecaster

A machine learning project to forecast potential system threats using historical data. The aim is to predict whether a given system state will result in a threat (binary classification).

## 📌 Problem Statement

The goal is to build a model that accurately classifies whether a system is under threat (`target = 1`) or not (`target = 0`) based on various system parameters and logs.

##  Exploratory Data Analysis (EDA)

- Missing values check
- Data type distribution
- Descriptive statistics
- Target class imbalance visualization

## 🛠 Preprocessing Pipeline

1. **Missing Values**: 
   - Numeric: Imputed using mean
   - Categorical: Imputed using most frequent value

2. **Time Feature Extraction**: 
   - Extracted `Month` from `DateAS`

3. **Categorical Encoding**: 
   - One-hot encoding (low cardinality)
   - Frequency encoding (high cardinality)

4. **Scaling**: 
   - Applied `RobustScaler` on numeric features

5. **Feature Selection**:
   - Remove low-cardinality columns (only one unique value)
   - Remove highly correlated features
   - Retain only features with correlation to target > 0.005
   - Remove low-variance features using `VarianceThreshold`

6. **Final Cleanup**:
   - Clean column names
   - Align train and test columns

## 🤖 Models Used

- **LightGBM (LGBMClassifier)**:
  - For feature importance analysis and classification

- **XGBoost (XGBClassifier)**:
  - Optional model used during hyperparameter tuning (commented out in base script)

## Feature Importance

Visualizes the top 30 most important features using LightGBM’s feature importances to interpret which system parameters most contribute to threats.

##  Requirements

Make sure you have the following libraries installed:

```bash
pip install pandas numpy seaborn matplotlib lightgbm xgboost scikit-learn
```

## ▶️ How to Run

1. Clone this repository or copy the code into a script (`main.py`)
2. Place `train.csv` and `test.csv` in the working directory
3. Run the script:
```bash
python main.py
```


Let me know if you'd like to include things like model performance metrics, Kaggle submission details, or deployment instructions too!
