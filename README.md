# 🛒 Instacart Market Basket Analysis

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?style=flat&logo=streamlit&logoColor=white)](https://streamlit.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-In%20Progress-orange)]()

> **End-to-end data science project** on 3M+ Instacart grocery orders — from exploratory analysis to a deployed product recommendation engine.

---

## 🎯 Project Goal

Analyze real-world grocery purchase behavior to:
- Understand **when**, **how often**, and **what** customers buy
- Discover **product associations** (market basket rules)
- **Predict reorder probability** for any user-product pair
- Deploy an **interactive recommender app** for product cross-sell

---

## 📁 Project Structure

```
instacart-market-basket-analysis/
│
├── data/
│   ├── raw/                    # Original Kaggle CSVs (not tracked in git)
│   └── processed/              # Feature-engineered outputs
│
├── notebooks/
│   ├── 01_EDA.ipynb                        # Exploratory Data Analysis
│   ├── 02_feature_engineering.ipynb        # User, product & interaction features
│   ├── 03_association_rules.ipynb          # FP-Growth market basket rules
│   └── 04_reorder_prediction.ipynb         # XGBoost reorder classifier
│
├── src/
│   ├── data_loader.py          # Load & merge raw data files
│   ├── features.py             # Feature engineering functions
│   └── model.py                # Model training & evaluation
│
├── app/
│   └── streamlit_app.py        # Interactive product recommender
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

## 📊 Dataset

**Source:** [Instacart Market Basket Analysis — Kaggle](https://www.kaggle.com/competitions/instacart-market-basket-analysis/data)

| File | Description | Rows |
|------|-------------|------|
| `orders.csv` | Order metadata (user, time, days since prior) | 3.4M |
| `order_products__prior.csv` | Products in prior orders | 32.4M |
| `order_products__train.csv` | Products in train orders | 1.4M |
| `products.csv` | Product names & aisle/dept mapping | 49.7K |
| `aisles.csv` | Aisle labels | 134 |
| `departments.csv` | Department labels | 21 |

> ⚠️ Raw data files are not committed to this repo. Download from Kaggle and place in `data/raw/`.

---

## 🔍 Notebooks Overview

### 01 — Exploratory Data Analysis
- Order frequency by day of week and hour
- Reorder rate by product and aisle
- Top 20 most purchased products
- Days-since-prior-order distribution
- Department-level purchase patterns

### 02 — Feature Engineering
| Feature Group | Examples |
|--------------|---------|
| User-level | total orders, avg basket size, reorder ratio |
| Product-level | order count, reorder rate, avg add-to-cart position |
| User-Product | times bought, order rate, days since last purchase |

### 03 — Association Rules (Market Basket)
- FP-Growth algorithm via `mlxtend`
- Rules filtered by support ≥ 0.01, confidence ≥ 0.3, lift ≥ 1.5
- Top product pairs and cross-category associations visualized

### 04 — Reorder Prediction (ML)
- Binary classification: will user reorder product in next order?
- Model: XGBoost classifier
- Evaluation: F1-score, ROC-AUC, Precision-Recall curve
- Feature importance + SHAP analysis

---

## 📈 Key Findings

*(Updated as notebooks complete)*

- 🕗 Peak order times: **Sunday & Monday mornings (8–11 AM)**
- 🥦 Top reordered categories: **Produce, Dairy, Beverages**
- 🔁 ~59% of all products in an order are reorders
- 🤝 Strong association: *Organic Strawberries → Organic Raspberries* (lift: 4.2)
- 🎯 XGBoost reorder model AUC: **~0.84**

---

## 🚀 Running the Project

### 1. Clone the repo
```bash
git clone https://github.com/[your-handle]/instacart-market-basket-analysis.git
cd instacart-market-basket-analysis
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Add data
Download from [Kaggle](https://www.kaggle.com/competitions/instacart-market-basket-analysis/data) and place CSVs in `data/raw/`.

### 4. Run notebooks in order
Open in Google Colab or Jupyter and run `01 → 02 → 03 → 04`.

### 5. Launch the Streamlit app
```bash
streamlit run app/streamlit_app.py
```

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| Data Manipulation | pandas, NumPy |
| Visualization | Matplotlib, Seaborn, Plotly |
| ML | scikit-learn, XGBoost |
| Association Rules | mlxtend |
| Explainability | SHAP |
| App | Streamlit |

---

## 👤 Author

**Vigneshwaran Rajendran**  
[LinkedIn](https://linkedin.com/in/vigneshwaran06/) · [GitHub](https://github.com/Vigneshwarananandan) · [Email](mailto:saivignesh1296@gmail.com)

---

## 📄 License

MIT License — feel free to fork and build on it.
