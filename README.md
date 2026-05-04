# 🏠 Tashkent House Price Prediction

> A project for analyzing data and building an ML model to predict house prices in Tashkent

---

## 📊 Project Status

![Status](https://img.shields.io/badge/Status-🚀%20Learning-brightgreen?style=for-the-badge)
![Progress](https://img.shields.io/badge/Progress-70%25%20Baseline%20Evaluated-blue?style=for-the-badge)
![Dataset](https://img.shields.io/badge/Dataset-✅%20Loaded-success?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python&logoColor=white)

---

## 🎯 Project Goal

**Goal:** To build a high-quality machine learning model for predicting house prices in Tashkent

**Data Source:** Real data from the Tashkent housing market (Excel format)

---

## ✅ Completed Work

### 📥 STAGE 1: Loading and Understanding the Data
- ✨ Loaded the data from an Excel file (`tashkent_houses.xlsx`)
- 📋 Explored the dataset structure (shape, columns)
- 📝 Created column descriptions

### 🔍 STAGE 2: Exploratory Data Analysis (EDA)
- 📊 **Basic Statistics:** `describe()` - mean, min, and max values
- 🎯 **Null Value Check:** identified missing values using `isna().sum()`
- 🔗 **Correlation Analysis:** studied the relationship between features and price
- 🗑️ **Data Cleaning:** removed the address column (1 row = 1 address)

### 📈 STAGE 3: Data Visualization
- 📊 **Histograms:** distributions for all numeric features
- 🎨 **Scatter Plot:** price distribution on the location map
- 📶 **Bar Plot:** average price by floor
- 🔥 **Heatmap:** visualization of the correlation matrix
- 📐 **Pairplot:** relationships between features and price

### 🔧 STAGE 4: Data Preprocessing
- 🗂️ **Data Filtering:** limited price to ≤400,000 and size to ≤350 sq.m for better prediction accuracy
- ✂️ **Train/Test Split:** split data into training and test sets (80/20) with stratification by district
- 🔄 **Imputation:** handled missing values using mean imputation
- 🔢 **Encoding:** applied Ordinal and OneHot encoding for categorical features (district)
- ⚙️ **Feature Engineering:** added custom features (room_size = size/rooms, distance_to_center using Haversine formula)
- 📏 **Scaling:** applied MinMaxScaler and StandardScaler for feature normalization
- 💾 **Data Saving:** saved processed data to CSV format

### 🧪 STAGE 5: Training Pipeline and Baseline Models
- 🔁 **Pipeline:** created a numeric pipeline with custom feature engineering and StandardScaler
- 🏷️ **ColumnTransformer:** combined numeric preprocessing with OneHot encoding for district
- ✅ **Pipeline Check:** verified that `full_pipeline.fit_transform(X_train)` works successfully
- 🤖 **Models:** trained Linear Regression, Decision Tree, and Random Forest models
- 📏 **Evaluation:** compared baseline models using RMSE
- 🔍 **Cross-Validation:** used `cross_val_score` to validate baseline models
- 🧾 **Sample Prediction:** compared predicted prices with actual prices on test samples
- 🏆 **Best Baseline:** Random Forest Regressor (`Test RMSE: 16200.90`)

---

## 📁 Project Structure

```
first-ml-training/
├── 📄 README.md                          # Information about the project
├── 📊 data/
│   ├── raw/
│   │   └── tashkent_houses.xlsx          # Raw data
│   └── processed/
│       └── tashkent_houses.csv           # Processed and cleaned data
├── 🤖 models/                            # Model artifacts (not saved yet)
└── 📓 notebooks/
    ├── 01_data_info.ipynb                # EDA Jupyter notebook
    ├── 02_data_Preprocessing.ipynb       # Data preprocessing Jupyter notebook
    └── 03_data_training.ipynb            # Training pipeline Jupyter notebook
```

---

## 🛠 Technologies Used

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)
![Seaborn](https://img.shields.io/badge/Seaborn-blue?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

---

## 📊 Dataset Information

| Parameter | Value |
|----------|--------|
| **Raw dataset** | 7421 rows, 9 columns |
| **Processed dataset** | 7405 rows, 8 columns |
| **Data types** | String, Integer, Float |
| **Null values** | None |
| **Location** | Tashkent city |
| **House types** | All types (private houses, multi-story apartments) |
| **Filtered** | Price ≤400,000, Size ≤350 sq.m |

---

## 🔑 Main Variables

| Variable | Description |
|-------------|---------|
| **district** | District where the house is located |
| **rooms** | Number of rooms |
| **size** | House area (sq. m) |
| **level** | Floor where the house is located |
| **max_levels** | Total number of floors |
| **price** | House price (target variable) |
| **lat** | Latitude coordinate |
| **lng** | Longitude coordinate |

---

## 🚀 Next Steps

- [x] Train baseline models (Linear Regression, Decision Tree, Random Forest)
- [x] Evaluate baseline models with RMSE
- [x] Add cross-validation for baseline models
- [ ] Analyze errors (MAE, R², residuals)
- [ ] Tune Random Forest hyperparameters
- [x] Save the trained models to the `models/` folder
- [ ] Deploy the best model

---

## 📝 Note

*Project development process: Data analysis → Feature engineering → Data preprocessing → Model training → Prediction*
model

---

## 📝 Note

*Project development process: Data analysis → Feature engineering → Data preprocessing → Model training → Prediction*
