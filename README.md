# 📈 Sales Forecast ML

![Python](https://img.shields.io/badge/python-3.11%2B-3776AB?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.4%2B-F7931E?logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-2.2%2B-150458?logo=pandas&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?logo=powerbi&logoColor=black)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-in%20development-yellow)

> 🇧🇷 Versão em português: [README.md](./README_PT.md)

> **Sales Dashboard with ML-Based Demand Forecasting.**
>
> A complete sales analytics system for a fictional e-commerce, combining Machine Learning models (customer segmentation, demand forecasting, and anomaly detection) in Python with an interactive Power BI dashboard.

---

## 📋 Contents

- [About](#-about)
- [Tech Stack](#-tech-stack)
- [Machine Learning Models](#-machine-learning-models)
- [Features](#-features)
- [Power BI Integration](#-power-bi-integration)
- [How to Run](#-how-to-run)
- [Methodology](#-methodology)
- [References](#-references)

---

## 💡 About

This project simulates the scenario of an e-commerce business that needs to turn raw sales data into business decisions. Based on the historical record of orders, customers, and products, the system:

1. **Segments customers** by purchasing behavior (Recency, Frequency, Monetary — RFM), using unsupervised learning.
2. **Forecasts future sales demand** based on historical and seasonal variables, using supervised learning.
3. **Detects anomalies** in transactions or sales patterns that fall outside expected behavior.

The results of each step are exported and consumed by a Power BI dashboard, bridging business visualization with ML output — including Python scripts run directly inside Power Query and Python visuals embedded in the report.

Since this is a learning project, development is split into **4 branches**, each representing a maturity stage of the project (data/EDA → segmentation → forecasting/anomalies → final Power BI integration).

---

## 🚀 Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Analysis & Modeling** | Python 3.11+ |
| **Visualization/BI** | Power BI Desktop |
| **Python Libraries** | Pandas, NumPy, scikit-learn, Matplotlib, Seaborn, Joblib |
| **Model Persistence** | Joblib (serialization of trained models) |
| **ML → BI Data Exchange** | `.csv` files |

---

## 🧠 Machine Learning Models

| Model | Learning Type | Application |
| :--- | :--- | :--- |
| **K-Means** | Unsupervised | Customer segmentation via RFM |
| **Random Forest Regressor** | Supervised | Sales/demand forecasting |
| **Isolation Forest** | Unsupervised | Anomaly detection in sales |

**Machine Learning concepts covered:**

- Unsupervised learning (clustering)
- Supervised learning (regression)
- Data normalization (`StandardScaler`)
- Choosing the optimal number of clusters (Elbow Method)
- Cross-validation and regression metrics (RMSE, MAE, R²)
- Feature importance with Random Forest

---

## ✨ Features

| Feature | Description | Status |
| :--- | :--- | :---: |
| **Data Preprocessing** | Cleaning, handling, and normalization of the sales dataset | 🔜 |
| **RFM Segmentation (K-Means)** | Grouping customers by Recency, Frequency, and Monetary value | 🔜 |
| **Sales Forecasting (Random Forest)** | Future demand estimation with evaluation metrics | 🔜 |
| **Anomaly Detection (Isolation Forest)** | Identifying outliers in transactions/sales | 🔜 |
| **Results Export (.csv)** | Generating files consumed by Power BI | 🔜 |
| **Power BI Dashboard** | Consolidated view of sales, clusters, and anomalies | 🔜 |

> Status will be updated as each branch/stage of the project is completed.

---

## 🔗 Power BI Integration

- **CSV Export** — ML results (clusters, forecasts, anomalies) are exported as `.csv` and imported directly into Power BI.
- **Python scripts in Power Query** — transformations and calculations can be run via Python inside Power Query itself.
- **Python visuals in the report** — charts generated with Matplotlib/Seaborn embedded as native Power BI visuals.

---

## ⚡ How to Run

### Prerequisites
- [Python 3.11+](https://www.python.org/)
- [Power BI Desktop](https://www.microsoft.com/power-platform/products/power-bi/desktop) (Windows)

### Step by Step

1. **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/sales-forecast-ml.git
    cd sales-forecast-ml
    ```

2. **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # Windows: venv\Scripts\activate
    ```

3. **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4. **Run the ML pipeline scripts/notebooks:**
    ```bash
    python src/run_pipeline.py
    ```
    *This generates the `.csv` files with clusters, forecasts, and anomalies in the `/output` folder.*

5. **Open the dashboard in Power BI:**
    - Open `dashboard/sales_dashboard.pbix`
    - Refresh the data source pointing to `/output`

---

## 📐 Methodology

### RFM Segmentation (K-Means)
Each customer is described by three variables — **Recency**, **Frequency**, and **Monetary value** — normalized with `StandardScaler` before clustering. The optimal number of clusters (*k*) is determined using the **Elbow Method**, observing the drop in inertia (WCSS) as *k* increases.

### Sales Forecasting (Random Forest Regressor)
The model is trained on historical and seasonal sales variables. Performance is validated through **cross-validation**, using the following metrics:

```
RMSE — Root Mean Squared Error
MAE  — Mean Absolute Error
R²   — Coefficient of Determination
```

The relevance of each variable is assessed through **feature importance**, native to Random Forest.

### Anomaly Detection (Isolation Forest)
Transactions or sales volumes outside the normal pattern are isolated based on how easily samples can be separated across random trees — anomalous samples tend to be isolated with fewer splits.

---

## 📚 References

- **Hughes, A. M. (1994)** — *Strategic Database Marketing* (origin of the RFM model)
- **Breiman, L. (2001)** — *Random Forests*, Machine Learning Journal
- **Liu, F. T., Ting, K. M., & Zhou, Z.-H. (2008)** — *Isolation Forest*, IEEE ICDM
- **Pedregosa et al. (2011)** — *Scikit-learn: Machine Learning in Python*, JMLR
- **Microsoft (2024)** — Power BI: Run Python scripts in Power Query