<div align="center">

# 🏡 Tashkent Real Estate: Price Prediction ML Pipeline

*An End-to-End Machine Learning Project for Predicting Housing Prices in Tashkent City.*

[![Status](https://img.shields.io/badge/Status-🚀_Active-brightgreen?style=for-the-badge)](https://github.com/)
[![Progress](https://img.shields.io/badge/Progress-85%25_Models_Saved-blue?style=for-the-badge)](https://github.com/)
[![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)

</div>

---

## 📖 Table of Contents
1. [🎯 Project Overview](#-project-overview)
2. [📊 Dataset Information](#-dataset-information)
3. [🧠 Methodology & Pipeline](#-methodology--pipeline)
   - [Exploratory Data Analysis (EDA)](#1️⃣-exploratory-data-analysis-eda)
   - [Data Preprocessing](#2️⃣-data-preprocessing--feature-engineering)
   - [Modeling & Evaluation](#3️⃣-modeling--evaluation)
4. [📁 Project Structure](#-project-structure)
5. [🏆 Results](#-results)
6. [🚀 Next Steps](#-next-steps)

---

## 🎯 Project Overview

This project aims to build a robust **Machine Learning Pipeline** capable of predicting real estate prices in Tashkent, Uzbekistan, based on property features such as location, size, and number of rooms. By leveraging data analysis, geospatial feature engineering, and advanced regression models, the system helps estimate fair market values for different types of properties.

---

## 📊 Dataset Information

The data comes from real listings in the Tashkent housing market. 

| **Metric** | **Value** |
| :--- | :--- |
| 🗃️ **Raw Rows** | 7,421 |
| 🧹 **Processed Rows** | 7,405 (Filtered outliers) |
| 📍 **Location** | Tashkent City, Uzbekistan |
| 🎯 **Target Variable** | `price` (USD) |

### 🔑 Core Features
- `address`, `district` - Categorical location data.
- `rooms` - Number of rooms.
- `size` - Total area of the property (sq.m).
- `level`, `max_levels` - Current floor and total floors in the building.
- `lat`, `lng` - Geospatial coordinates (Latitude & Longitude).

---

## 🧠 Methodology & Pipeline

The project development was divided into several focused stages inside Jupyter Notebooks:

### 1️⃣ Exploratory Data Analysis (EDA)
> *Found in `01_data_info.ipynb`*
- **Statistical Summaries:** Extracted basic distributions (`mean`, `min`, `max`).
- **Data Cleaning:** Validated null counts (no nulls found) and dropped the high-cardinality `address` column.
- **Visualizations:**
  - 📊 **Histograms** for numeric feature distributions.
  - 🎨 **Geospatial Scatter Plots** mapping price density across Tashkent coordinates.
  - 🔥 **Correlation Heatmaps** and **Pairplots** to identify features heavily influencing `price`.

### 2️⃣ Data Preprocessing & Feature Engineering
> *Found in `02_data_Preprocessing.ipynb`*
- **Outlier Removal:** Filtered anomalies (`price` $\le$ 400,000 and `size` $\le$ 350 sq.m) to enhance model robustness.
- **Stratified Split:** Executed an 80/20 train-test split, stratified by `district` to ensure proportional regional representation.
- **Custom Transformers (Feature Engineering):** 
  - 📏 `room_size`: Calculated as $\text{size} / \text{rooms}$.
  - 🗺️ `distance_to_center`: Computed spatial distance from the exact center of Tashkent using the **Haversine formula**.
- **Transformation Pipeline:**
  - Standardized numeric features using `StandardScaler`.
  - Encoded categorical features (`district`) using `OneHotEncoder`.
  - Combined transformations elegantly using Scikit-Learn's `ColumnTransformer`.

### 3️⃣ Modeling & Evaluation
> *Found in `03_data_training.ipynb`*
Three baseline algorithms were trained and cross-validated using a `Pipeline` integration:
1. **Linear Regression**
2. **Decision Tree Regressor**
3. **Random Forest Regressor** 🌟 (Best Performer)

Each model was strictly evaluated utilizing `Cross-Validation (CV)` and `Root Mean Squared Error (RMSE)`. The resulting models were serialized for deployment.

---

## 📁 Project Structure

```text
first-ml-training/
├── 📄 README.md                          # You are here!
├── 📊 data/
│   ├── raw/
│   │   └── tashkent_houses.xlsx          # Initial raw dataset
│   └── processed/
│       └── tashkent_houses.csv           # Cleaned dataset ready for modeling
├── 🤖 models/                            
│   ├── random_forest_model.jbl           # Serialized RF model (Joblib)
│   ├── logistic_regression_model.jbl     # Serialized LR model (Joblib)
│   └── decision_tree_model.pkl           # Serialized DT model (Pickle)
└── 📓 notebooks/
    ├── 01_data_info.ipynb                # Data Exploration & Visualization
    ├── 02_data_Preprocessing.ipynb       # Feature Engineering & Pipelines
    └── 03_data_training.ipynb            # Model Training & Cross Validation
```

---

## 🏆 Results

Upon evaluating the models on the hold-out test set, the **Random Forest Regressor** significantly outperformed the other baselines:

- 🏅 **Best Model:** `Random Forest Regressor`
- 🎯 **Test RMSE Score:** **`16,200.90`** (Outstanding baseline accuracy for real estate pricing)

All trained artifacts have been successfully exported to the `models/` directory using `joblib` and `pickle` for future REST API integration.

---

## 🚀 Next Steps

- [x] Full EDA and Outlier filtering.
- [x] Geospatial feature engineering (Haversine distance).
- [x] Train baseline regression models.
- [x] Model evaluation with CV and RMSE.
- [x] Export winning models to `.jbl` / `.pkl`.
- [ ] 🔄 **Hyperparameter Tuning** (GridSearchCV / RandomizedSearchCV for Random Forest).
- [ ] 📈 **Advanced Error Analysis** (Evaluate Residuals, R² Score, MAE).
- [ ] 🌐 **Deployment** (Wrap the Random Forest pipeline in a FastAPI or Flask web service).

---
<div align="center">
  <i>Built with ❤️ utilizing</i><br><br>
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy" />
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas" />
  <img src="https://img.shields.io/badge/Scikit_Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn" />
  <img src="https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white" alt="Seaborn" />
</div>