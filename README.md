# 🌍 LSTM for Air Quality Prediction

**Author:** Gervasius Russell
**NIM:** 2702257450
**Major:** Data Science, BINUS University

---

## 📌 Project Overview

This project applies **Long Short-Term Memory (LSTM)** networks to predict **Air Temperature (°C)** from air quality time series data.

The workflow covers:

1. **Exploratory Data Analysis (EDA)**
2. **Data Cleaning & Imputation**
3. **Normalization & Sequence Generation**
4. **LSTM Modeling** (Baseline, Modified, Hyperparameter-tuned)
5. **Evaluation & Comparison**
6. **Discussion on Multivariate Time Series**

---

## ⚙️ Tech Stack

* **Python** (Pandas, NumPy, Matplotlib, Seaborn)
* **Missingno** (null value visualization)
* **Scikit-learn** (MinMaxScaler, evaluation metrics)
* **TensorFlow/Keras** (LSTM, Dense, Dropout, EarlyStopping)
* **Keras Tuner** (Hyperparameter optimization)

---

## 🔍 Workflow Summary

### 1. Exploratory Data Analysis

* Inspected missing values (using `missingno`).
* Selected **To Date** as the primary timestamp index.
* Observed **seasonality**, **daily patterns**, and occasional outliers.

### 2. Preprocessing

* Imputation: **time-based interpolation + bfill/ffill**.
* Normalization: **MinMaxScaler** to [0, 1].
* Data split: **80/10/10** (train/val/test).
* Sequence generation: sliding window with 5-hour lookback.

### 3. Models

* **Baseline LSTM**:

  * LSTM(10) → Dense(1, linear)
  * Simple and effective.

* **Modified LSTM**:

  * LSTM(32) → Dropout(0.1) → Dense(16, relu) → Dense(1)
  * Added regularization + complexity for better generalization.

* **Hyperparameter-Tuned LSTM (Hyperband)**:

  * Searched units (32–128), dropout (0.1–0.5), learning rate.
  * EarlyStopping applied for efficiency.

### 4. Evaluation Metrics

* **MAE** – Mean Absolute Error
* **MSE** – Mean Squared Error
* **R²** – Variance explained

| Model       | MAE     | MSE     | R² Score |
| ----------- | ------- | ------- | -------- |
| Baseline    | 0.01305 | 0.00037 | 0.95801  |
| Modified    | 0.01267 | 0.00035 | 0.96054  |
| Hypertuning | 0.01324 | 0.00036 | 0.95866  |

✅ **Best model: Modified LSTM** (lowest MAE, highest R²).

---

## 📊 Key Insights

* **Baseline LSTM** already performed strongly (R² ~95%).
* **Modified LSTM** with dropout & dense layer achieved **best generalization**.
* **Hypertuning** didn’t outperform manual tuning — simple models can be optimal.
* Air temperature prediction can be **extended to multivariate time series**, since features like RH, CO, SO₂, WS, SR all correlate with AT.

---

## 🚀 How to Run

1. Clone repository:

   ```bash
   git clone https://github.com/<your-username>/lstm-air-quality.git
   cd lstm-air-quality
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Run Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

---

## 🎥 Demo

📺 [Video Presentation](https://drive.google.com/file/d/1TohnYrzabdDWBkG_WOpImk6XItmcIVCd/view?usp=sharing)

---

✍️ **Author**: Gervasius Russell
📌 **Goal**: Build and evaluate LSTM models for air quality time series forecasting.
