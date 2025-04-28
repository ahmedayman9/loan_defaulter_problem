# 📊 Loan Defaulter Prediction Project (Before and After Data Merging)

## 🧠 Problem Formulation

Financial institutions face significant losses due to loan defaults. Traditional credit scoring methods often miss subtle risk patterns, especially when historical behavior is fragmented across multiple systems.  
To mitigate credit risk and protect business margins, it is crucial to integrate **historical payment behavior** directly into the **loan approval decision-making** process.

---

## 🏢 Business Understanding

- **Industry Context**:  
  In the lending industry, reducing the default rate is critical to maintaining profitability and liquidity.  
  A customer's **past default behavior** is often the strongest predictor of future default risk.

- **Problem Context**:  
  Lenders often assess new applications based on limited information, missing out on hidden historical risks.  
  This can cause **high-risk customers** to receive loans, leading to increased **Non-Performing Loans (NPLs)**.

---

## 🎯 Business Objectives

- **Primary Objective**:  
  Develop a **predictive model** that flags risky customers at the time of loan application by analyzing **both current application data and past payment behavior**.

- **Sub-Objectives**:
  - **Merge** historical repayment data with current loan applications.
  - **Identify** customers with prior negative payment behaviors.
  - **Create** a decision feature (`DECISION`) for automatic risk flagging.
  - **Build** accurate machine learning models to predict default risk.
  - **Optimize** model thresholds to maximize recall without heavily sacrificing precision.
  - **Minimize** potential financial losses by proactively rejecting risky applicants.

---

## 🚀 Project Workflow

### 1. Initial Analysis (Before Merging)

- **Datasets**:
  - Primary Loan Application dataset.
  - Customer Payment Behavior dataset.
- **Key Actions**:
  - Analyzed separate datasets individually.
  - Detected and flagged customers with past **payment issues** (defaults, frauds, late payments).
  - Performed preliminary EDA (Exploratory Data Analysis) on raw features.
  - Designed an initial customer risk scoring strategy.

### 2. Final Analysis (After Merging)

- **Merged** customer application data with historical payment behavior.
- Consolidated customer information into a **single dataset** with a unified **risk profile**.
- Introduced the key feature:
  - **`DECISION`**:
    - `0` → Risky customer (has historical issues)
    - `1` → Non-risky customer (no significant past issues)

---

## 📚 Dataset Details

- **Source Files**:
  - `ApplicationData.csv`
  - `previous_application.csv`
- **Final Merged Dataset**:
  - `Merged.csv`

🔗 Dataset available at: [Home Credit Default Risk on Kaggle](https://www.kaggle.com/datasets/gauravduttakiit/loan-defaulter/data?select=previous_application.csv)

---

## 📊 Exploratory Data Analysis (EDA)

- Distribution of numerical features:
  
  ![Feature Distribution](images/feature_distribution.png)

- Boxplots to detect outliers:
  
  ![Boxplot Example](images/boxplot_example.png)

- Correlation analysis with the target variable:
  
  ![Correlation Heatmap](images/correlation_heatmap.png)

---

## 🛠️ Machine Learning Approach

### Preprocessing

- **Label Encoding** for binary categorical columns.
- **Ordinal Encoding** for ordered categorical columns (e.g., education levels).
- **One-Hot Encoding** for multi-class categorical columns.

### Handling Imbalanced Data

- **SMOTE** (Synthetic Minority Oversampling)
- **ADASYN** (Adaptive Synthetic Sampling)

### Models Trained

- **Random Forest Classifier**  
  (Hyperparameter tuning using GridSearchCV)
- **XGBoost Classifier**  
  (Tuned `scale_pos_weight` to address class imbalance, threshold tuning)

### Model Evaluation

- Metrics:
  - Accuracy
  - Precision, Recall, F1-Score
  - ROC AUC Score
- Visualization:
  - Confusion Matrix
  - ROC Curves
  - Precision-Recall Curves

---

## 📈 Model Evaluation Results

- Confusion Matrix:

  ![Confusion Matrix](images/confusion_matrix.png)

- ROC Curve:

  ![ROC Curve](images/roc_curve.png)

- Precision-Recall Curve:

  ![Precision-Recall Curve](images/precision_recall_curve.png)

- Top 20 Important Features:

  ![Feature Importance](images/feature_importance.png)

---

## 🏆 Key Results

| Model            | Description                         | Accuracy (Approx.) |
|------------------|-------------------------------------|--------------------|
| Random Forest    | After Hyperparameter Tuning         | ~90%               |
| XGBoost          | After SMOTE + Threshold Optimization| **~92%**            |

- XGBoost achieved **higher recall** and better Precision-Recall balance after threshold optimization.
- Feature Importance analysis revealed top drivers influencing loan default risk.

