# 🩺 Diabetes Prediction Using Machine Learning

### A Comparative Study of Classification Algorithms and Feature Engineering

<p align="center">
  <strong>Exploratory Data Analysis · Machine Learning · Feature Engineering · Model Evaluation</strong>
</p>

---

## 📌 Overview

Can machine learning help identify patterns associated with diabetes?

This project explores diabetes prediction through a comparative study of five classification algorithms, supported by exploratory data analysis, data preprocessing, feature engineering, and performance evaluation.

The primary objective is to investigate how different feature sets influence classification performance and to compare locally obtained experimental results with values reported in a published research paper.

Rather than focusing on a single model, this project evaluates multiple approaches under a consistent experimental setup.

## ✨ Key Highlights

- Comprehensive Exploratory Data Analysis (EDA)
- Data quality inspection and missing-value handling
- Prevention of data leakage through training-only imputation
- Three feature-set experiments
- Five machine learning classification algorithms
- Multiple evaluation metrics
- Confusion matrix analysis
- Visual comparison of experimental and published results

## 🧠 Machine Learning Models

Five classification algorithms are implemented:

| Model                           | Configuration                                 |
| ------------------------------- | --------------------------------------------- |
| K-Nearest Neighbors (KNN)       | 5 neighbors                                   |
| Random Forest (RF)              | 300 trees                                     |
| Support Vector Machine (SVM)    | RBF kernel                                    |
| Artificial Neural Network (ANN) | Hidden layers: (16, 8)                        |
| Decision Tree (DT)              | Default configuration with fixed random state |

Feature scaling is applied to KNN, SVM, and ANN using StandardScaler within Scikit-learn pipelines.

## 📊 Dataset

The project uses a diabetes dataset containing:

- 768 records
- 8 input features
- 1 target variable

### Features

| Feature                  | Description                    |
| ------------------------ | ------------------------------ |
| Pregnancies              | Number of pregnancies          |
| Glucose                  | Plasma glucose concentration   |
| BloodPressure            | Diastolic blood pressure       |
| SkinThickness            | Triceps skinfold thickness     |
| Insulin                  | 2-hour serum insulin           |
| BMI                      | Body Mass Index                |
| DiabetesPedigreeFunction | Diabetes pedigree function     |
| Age                      | Age in years                   |
| Outcome                  | Diabetes classification target |

The target variable is binary:

- 0 — Non-diabetic
- 1 — Diabetic

## 🔬 Methodology

### 1. Exploratory Data Analysis

The dataset is explored through descriptive statistics, data-quality inspection, target distribution analysis, and visualizations of important clinical variables.

### 2. Data Preprocessing

Zero values in the following columns are treated as invalid measurements:

- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI

These values are converted to missing values and handled using median imputation.

Important: The dataset is split before fitting the imputer. Median values are learned exclusively from the training set and then applied to the test set to prevent data leakage.

### 3. Train-Test Split

The dataset is divided using:

- Training set: 70%
- Testing set: 30%
- Random state: 42
- Stratified splitting

### 4. Feature Engineering

Two additional features are introduced based on the reference research:

- BP_GT80: Indicates whether BloodPressure is greater than 80.
- BP80_Glucose105: Indicates whether BloodPressure is greater than 80 and Glucose is greater than 105.

### 5. Experimental Design

Three experiments are conducted:

| Experiment | Feature Set                             |
| ---------- | --------------------------------------- |
| Table 3    | Base features + two engineered features |
| Table 4    | Base features only                      |
| Table 5    | Reduced feature set                     |

The reduced feature set excludes SkinThickness and DiabetesPedigreeFunction.

All experiments use the same train-test split and training-only imputation strategy.

## 📈 Evaluation Metrics

Each model is evaluated using four classification metrics:

- Accuracy: Overall proportion of correct predictions.
- Precision: Proportion of positive predictions that are correct.
- Recall: Proportion of actual positive cases correctly identified.
- F1-score: Harmonic mean of precision and recall.

Confusion matrices are also generated to provide a more detailed view of classification performance.

## 📚 Research Comparison

This project references:

Nahzat, S., & Yağanoğlu, M. (2021).

The published performance values are presented separately from the results generated by the notebook.

An important distinction is maintained throughout the project:

- Experimental metrics are calculated from the notebook's actual predictions.
- Published metrics are transcribed from the reference paper.

The reported Random Forest accuracy of 88.31% for the experiment with two engineered features is a published reference value, not a result claimed by this local experiment.

Since the paper does not specify every implementation detail, exact reproduction of its reported scores cannot be guaranteed.

This distinction helps maintain experimental transparency and scientific integrity.

## 🛠️ Technologies & Libraries

| Technology       | Purpose                                       |
| ---------------- | --------------------------------------------- |
| Python           | Core programming language                     |
| Jupyter Notebook | Interactive experimentation                   |
| NumPy            | Numerical operations                          |
| Pandas           | Data manipulation                             |
| Matplotlib       | Data visualization                            |
| Seaborn          | Statistical visualization                     |
| Scikit-learn     | Preprocessing, classification, and evaluation |

## 📁 Project Structure

`text
Diabetes-Prediction/
│
├── dataset/
│ └── diabetes (1).csv
│
├── notebooks/
│ └── prediction-diabetes.ipynb
│
└── README.md
