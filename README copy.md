# 🎯 Career Switch Prediction

> A machine learning project to predict whether an individual is likely to change their career, based on demographic, educational, and professional data.

**Course:** CSE422 – Artificial Intelligence Lab  
**Institution:** BRAC University, Department of Computer Science and Engineering  
**Submission Date:** September 3, 2026

---

## 📌 Problem Statement

Employee turnover and career switching pose significant challenges and costs to organizations worldwide. This project builds a binary classification pipeline to predict the target variable `will_change_career` (0 = No Switch, 1 = Will Switch), helping HR departments proactively identify potential career switchers.

---

## 📂 Repository Structure

```
career-switch-prediction/
│
├── career-switch-prediction.ipynb        # Main Jupyter Notebook (all code & visualizations)
├── Career_Switch_Prediction_Dataset.csv  # Dataset (5,000 records, 14 features)
├── career-switch-prediction.pdf          # Final IEEE-format project report (PDF)
├── career-switch-prediction.docx         # Final project report (editable Word format)
└── Lab-Learning materials/               # CSE422 course reference materials
```

---

## 📊 Dataset

| Property | Details |
|---|---|
| **File** | `Career_Switch_Prediction_Dataset.csv` |
| **Records** | 5,000 |
| **Features** | 14 (13 predictors + 1 target) |
| **Target Variable** | `will_change_career` (Binary: 0 / 1) |
| **Feature Types** | 3 Quantitative, 11 Categorical |
| **Class Distribution** | Class 0: 3,738 · Class 1: 1,262 (Imbalanced) |

**Features:** `city`, `city_development_index`, `gender`, `relevent_experience`, `enrolled_university`, `education_level`, `major_discipline`, `experience`, `company_size`, `company_type`, `last_new_job`, `training_hours`

---

## ⚙️ Methodology

### Pre-processing (Leak-Free Pipeline)
The dataset was split **before** any imputation or scaling to strictly prevent data leakage.

| Step | Problem | Solution |
|---|---|---|
| Missing Values | Null values in `gender`, `major_discipline`, `company_size`, etc. | Median (numeric) / Mode (categorical) imputation on training set only |
| Categorical Encoding | String labels not usable by ML models | `LabelEncoder` fitted on training data |
| Feature Scaling | Drastically different feature scales | `StandardScaler` fitted on training data |

### Dataset Splitting
- **80% Training / 20% Testing** with stratified sampling
- **Random Undersampling** applied to the training set only (majority class reduced to match minority class) to address class imbalance

---

## 🤖 Models

Seven models were trained and evaluated:

| Type | Model |
|---|---|
| Unsupervised | K-Means Clustering (K=2, visualized via 2D PCA) |
| Supervised | K-Nearest Neighbors (KNN) |
| Supervised | Decision Tree |
| Supervised | Logistic Regression |
| Supervised | Linear Regression (thresholded at 0.5) |
| Supervised | Naive Bayes (GaussianNB) |
| Supervised | Neural Network (MLPClassifier) |

---

## 📈 Results

| Model | Accuracy | Precision | Recall | AUC |
|---|:---:|:---:|:---:|:---:|
| KNN | 62.20% | 36.30% | 66.27% | 0.6752 |
| Decision Tree | 62.10% | 35.40% | 61.11% | 0.6175 |
| Logistic Regression | 70.90% | 44.31% | 60.32% | 0.7126 |
| **Linear Regression** | **71.50%** | **45.02%** | **59.13%** | **0.7130** |
| Naive Bayes | 69.70% | 43.38% | 66.27% | 0.7023 |
| Neural Network | 65.30% | 38.88% | 65.87% | 0.7062 |

> **Linear Regression** (thresholded) achieved the highest accuracy (71.50%), while **Logistic Regression** provided the best overall balance of Recall and AUC.  
> Linear Regression regression metrics: R² = -0.1185, MSE = 0.2108.

---

## 📉 Visualizations (from Notebook)

| Fig. | Description |
|---|---|
| Fig. 1 | Bar Chart of Target Classes (Class Imbalance) |
| Fig. 2 | Feature Correlation Heatmap |
| Fig. 3 | K-Means Clusters (2D PCA Projection) |
| Fig. 4 | Prediction Accuracy Comparison – All Models |
| Fig. 5 | Confusion Matrices – All Six Supervised Models |
| Fig. 6 | ROC Curves – All Models |

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/career-switch-prediction.git
   cd career-switch-prediction
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

3. **Open the notebook**
   ```bash
   jupyter notebook career-switch-prediction.ipynb
   ```

4. **Run all cells** — the notebook will load the CSV from the same directory, preprocess the data, train all models, and generate all figures automatically.

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-f7931e?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-Data-150458?logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4c72b0)

---

## 📄 Report

The full IEEE-format project report is available in this repository:
- **PDF:** [`career-switch-prediction.pdf`](./career-switch-prediction.pdf)
- **DOCX:** [`career-switch-prediction.docx`](./career-switch-prediction.docx)

---

## 👤 Author

**Prantik**  
Department of Computer Science and Engineering  
BRAC University

---

*CSE422: Artificial Intelligence Lab Project — BRAC University, 2026*
