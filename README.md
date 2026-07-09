# 🌾 Agricultural Crop Yield Prediction Using Machine Learning

---

[![Project](https://img.shields.io/badge/project-Crop%20Yield%20Prediction-blue.svg)]() [![Language](https://img.shields.io/badge/language-Python-yellow.svg)]() [![License](https://img.shields.io/badge/license-MIT-green.svg)]()

A data-driven solution to estimate crop yields by analyzing environmental and farming factors — empowering farmers, agronomists, and policymakers to make better decisions.

---

## 📖 Project Overview

Accurate crop yield prediction helps optimize resource allocation, reduce waste, and increase food security. This project builds a complete machine learning pipeline to predict agricultural crop yield from features such as rainfall, temperature, soil type, fertilizer/irrigation usage, weather conditions, and days to harvest. The result is a reusable, explainable pipeline and notebooks that demonstrate how data science can support smarter agriculture.

---

## 🎯 Objectives

- Build a robust ML pipeline for crop yield prediction.
- Evaluate and compare regression models to find the best performer.
- Provide interactive visualizations and explainable feature insights.
- Deliver a reproducible notebook and artifacts suitable for a portfolio.

---

## ✨ Key Features

- End-to-end ML pipeline: data cleaning → modeling → evaluation.
- Interactive EDA using Plotly and Matplotlib.
- Feature engineering and selection for better generalization.
- Model comparison and explainability (feature importance).
- Notebook-friendly, reproducible, and recruiter-ready documentation.

---

## 📊 Dataset Description

Dataset contains rows of agricultural observations, each with the following features:

- Region
- Soil Type
- Crop
- Rainfall
- Temperature
- Fertilizer Used
- Irrigation Used
- Weather Condition
- Days to Harvest
- Yield (Target Variable)

Data cleaning steps performed: missing value handling, duplicate removal, encoding categorical variables, scaling numeric features, and feature selection.

---

## ⚙️ Technologies Used

- Python
- Pandas & NumPy
- Scikit-learn
- Matplotlib & Plotly
- Jupyter Notebook

---

## 🧠 Machine Learning Workflow

1. Data Loading
   - Load CSV(s) and validate schema, data types, and ranges.

2. Data Cleaning
   - Handle missing values (imputation strategies by column).
   - Remove duplicates, correct inconsistent labels.

3. Data Preprocessing
   - Convert categorical fields (Region, Soil Type, Crop, Weather Condition) using one-hot encoding or ordinal encoding where appropriate.
   - Feature scaling (StandardScaler or MinMaxScaler) for numeric inputs.

4. Feature Engineering
   - Derive interaction terms (e.g., rainfall × irrigation).
   - Aggregate temporal or regional statistics when available.
   - Use correlation analysis and importance measures for selection.

5. Exploratory Data Analysis (EDA)
   - Univariate: histograms, KDEs, boxplots to inspect distributions.
   - Bivariate: scatterplots and boxplots comparing features to yield.
   - Multivariate: correlation heatmap to detect collinearity.
   - Interactive plots with Plotly for deeper inspection.

6. Model Training
   - Split data into train/validation/test sets (stratify if needed).
   - Train baseline (Linear Regression) and ensemble models (Random Forest Regression).
   - Use cross-validation for robust evaluation.

7. Model Evaluation
   - Evaluate with regression metrics (R², MAE, RMSE).
   - Compare models on validation/test sets and choose best-performer.

8. Explainability & Insights
   - Present feature importance (coefficients for linear models, permutation/importances for tree models).
   - Interpret top drivers of yield (e.g., rainfall, fertilizer, days to harvest).

9. Deployment / Artifacts
   - Save best model artifact (.pkl) and provide inference example in notebook.

---

## 📈 Exploratory Data Analysis

Visualizations and their purpose:

- Histograms & KDEs — inspect distributions and skewness (e.g., rainfall, temperature).
- Boxplots — detect outliers and distribution by categorical groups (soil type, crop).
- Scatterplots — examine relationships (rainfall vs. yield, temperature vs. yield).
- Correlation Heatmap — identify multicollinearity and candidate features to drop/transform.
- Pairwise plots — visualize interactions among predictors.
- Interactive Plotly dashboards — allow dynamic filtering by region/crop for stakeholder exploration.

Each visualization is included in the Notebook with commentary and actionable insights (e.g., which features are most predictive and how outliers were treated).

---

## 🤖 Machine Learning Models

Models evaluated:
- Linear Regression — interpretable, performed best for this dataset due to linear relationships between features and yield.
- Random Forest Regression — robust and non-linear, used for comparison and feature importance.

Linear Regression emerged as the best-performing model on held-out test data for this dataset and preprocessing choices, providing both simplicity and interpretability.

---

## 📊 Model Performance Comparison

Summary of model behavior (qualitative):

| Model                   | Generalization | Interpretability | Use Case |
|------------------------:|:--------------:|:----------------:|:--------:|
| Linear Regression       | Best (on test) | High             | Production / Reporting |
| Random Forest Regression| Good           | Medium           | When non-linear effects matter |

Notes:
- Linear Regression provided strong predictive power and clear coefficients that explain how each input affects yield.
- Random Forest was useful to validate non-linear interactions and to cross-check feature importance.

---

## 🌱 Real World Applications

- Precision agriculture recommendations (optimal fertilizer and irrigation planning)
- Regional yield forecasting for supply chain and policy planning
- Crop insurance risk modeling and early warning systems
- Decision support for agronomists and farm managers

---

## 📂 Project Structure

Agricultural-Crop-Yield-Prediction/
│
├── Dataset/                 # Raw & processed datasets (CSV)
├── Notebook/                # Jupyter notebooks with EDA and modeling
├── Images/                  # Figures used in README and notebooks
├── Model/                   # Saved model artifacts (.pkl)
├── README.md
└── requirements.txt         # Reproducible environment

---

## 🚀 Getting Started (Reproduce the analysis)

1. Clone the repo
   ```bash
   git clone https://github.com/Muneeza-Siddiqui/crops-yield-prediction-project.git
   cd crops-yield-prediction-project
   ```

2. Create a virtual environment and install dependencies
   ```bash
   python -m venv .venv
   source .venv/bin/activate   # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. Open the main notebook
   ```bash
   jupyter notebook Notebook/Crop_Yield_Prediction.ipynb
   ```

4. Run cells in order to reproduce EDA, modeling, and results. The notebook contains explanations, visualizations, and model save/load examples.

---

## 🚀 How to Use the Trained Model (Example)

Example Python snippet to load and predict with a saved model artifact:

```python
import pandas as pd
import joblib

# Load model
model = joblib.load("Model/linear_regression_model.pkl")

# Example observation (same preprocessing must be applied)
sample = pd.DataFrame([{
    "Region": "RegionA",
    "Soil Type": "Loamy",
    "Crop": "Wheat",
    "Rainfall": 120.0,
    "Temperature": 25.0,
    "Fertilizer Used": 50,
    "Irrigation Used": 1,
    "Weather Condition": "Sunny",
    "Days to Harvest": 90
}])

# Apply same preprocessing (encoding, scaling) used during training
# preprocessed_sample = preprocess(sample)   # see notebook for preprocess()

# Predict
# prediction = model.predict(preprocessed_sample)
# print("Predicted yield:", prediction[0])
```

(See Notebook for full preprocessing pipeline and actual inference steps.)

---

## 🚧 Future Improvements

- Add temporally-aware models (time-series components) if multi-year data is available.
- Incorporate remote sensing (satellite NDVI) and weather forecasts for better early prediction.
- Integrate hyperparameter tuning (Optuna) and model ensembling.
- Create a simple web demo or dashboard for stakeholder interaction.
- Add unit tests and CI to ensure reproducibility and model stability.

---

## 💡 Learning Outcomes

- Applied end-to-end ML pipeline and reproducible practices.
- Gained hands-on experience with feature engineering and encoding strategies for mixed-type data.
- Learned to evaluate model trade-offs (interpretability vs. non-linear power).
- Built interactive EDA and actionable domain insights for agriculture.

---

## 👩‍💻 About the Author

**Muneeza Shehwar**  
BS Data Science Student  
Passionate about Artificial Intelligence, Machine Learning, Data Science, Python, and solving real-world problems through intelligent data-driven solutions. Actively building projects that bridge data science and societal impact.

---

## ⭐ Support

If you found this project useful or informative, please give it a star ⭐ — it helps visibility and supports my journey as a data scientist.

---

Thank you for exploring this project — feel free to open issues, suggest improvements, or request a walkthrough of the notebooks!
