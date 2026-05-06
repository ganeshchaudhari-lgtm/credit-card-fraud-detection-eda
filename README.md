
# 💳 credit-card-fraud-detection-eda

> Exploratory Data Analysis (EDA) on the IEEE/Kaggle Credit Card Fraud Detection dataset — uncovering class imbalance, transaction patterns, and feature relationships through 9+ targeted visualizations.

---

## 📌 Repository Name

**`credit-card-fraud-detection-eda`**

## 📝 Description

A comprehensive EDA notebook that dissects credit card transaction data to understand the nature of fraudulent vs. legitimate activity. Covers class imbalance analysis, temporal transaction patterns, amount distribution comparisons, PCA feature correlations, and multi-variable fraud profiling — all backed by carefully chosen chart types with documented reasoning.

---

## 📁 Project Structure

```
credit-card-fraud-detection-eda/
│
├── Fraud_detection.ipynb               # Main EDA notebook (13 cells, 9+ charts)
├── fraud_detection_charts_explanation.html  # Detailed chart-by-chart explanation
├── README.md                           # Project documentation
└── data/
    └── creditcard.csv                  # Source dataset (Kaggle — not included, see below)
```

---

## 📊 Visualizations Included

| # | Chart | Type | Purpose |
|---|-------|------|---------|
| 1 | Distribution of Fraud vs. Non-Fraud | Count Bar Chart | Reveal class imbalance |
| 2 | Percentage Distribution — Fraud vs. Non-Fraud | Pie Chart | Proportional perspective |
| 3 | Distribution of Transaction Amounts | Histogram + KDE | Amount distribution shape |
| 4 | Number of Transactions Over Time | Line Chart | Temporal fraud patterns |
| 5 | Transaction Amount vs. Time (by Class) | Scatter Plot | Joint amount-time clustering |
| 6 | Transaction Amount Distribution by Class | Box Plot | Statistical comparison |
| 7 | Correlation Matrix of Features | Heatmap | Multicollinearity, PCA validation |
| 8 | Distribution of Amounts by Class | Violin Plot | Full density shape per class |
| 9 | Cumulative Transaction Amount Over Time | Area Chart | Financial volume growth |
| + | Multi-Variable Bubble Chart (Bonus) | Bubble Chart | 4D fraud pattern (Time, Amount, Class, V14) |

---

## 🔍 Key Findings

- **Severe class imbalance** — fraudulent transactions represent only ~0.17% of the dataset, making accuracy alone a misleading metric; techniques like SMOTE or weighted loss functions are needed.
- **V1–V28 features** are PCA-anonymized components, largely uncorrelated by design, confirmed by the correlation heatmap.
- **V14** is among the PCA components most correlated with fraud and was used as the bubble size in the multi-variable chart to surface 4-dimensional fraud patterns.
- **Transaction amount** distributions differ between fraud and legitimate classes — box and violin plots reveal median, IQR, and density shape differences.
- **Temporal patterns** in fraud events can be identified through time-series line and scatter plots.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Core language |
| Pandas | Data loading and manipulation |
| NumPy | Numerical operations |
| Matplotlib | Base plotting |
| Seaborn | Statistical visualizations |
| Google Colab | Notebook runtime |

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/your-username/credit-card-fraud-detection-eda.git
cd credit-card-fraud-detection-eda
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn
```

### 3. Get the dataset

Download `creditcard.csv` from [Kaggle — Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) and place it in the `data/` folder.

> The dataset contains 284,807 transactions with 30 features (Time, Amount, V1–V28, Class).

### 4. Run the notebook

Open `Fraud_detection.ipynb` in Jupyter or Google Colab and run all cells.

```bash
jupyter notebook Fraud_detection.ipynb
```

---

## 📂 Dataset Description

| Feature | Description |
|---------|-------------|
| `Time` | Seconds elapsed between this and the first transaction |
| `Amount` | Transaction amount in euros |
| `V1–V28` | PCA-anonymized features (original features confidential) |
| `Class` | Target variable — `0` = Non-Fraud, `1` = Fraud |

**Source:** [ULB Machine Learning Group](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

---

## 📈 Sample Chart Insights

**Class Imbalance** — The count bar chart makes immediately clear that fraudulent transactions are a tiny minority. A model predicting "non-fraud" for every transaction would achieve ~99.8% accuracy — yet be completely useless for fraud detection.

**Correlation Heatmap** — V1–V28 show near-zero inter-feature correlation, confirming the PCA transformation preserved orthogonality. Time and Amount retain some correlation patterns with specific V components worth investigating for feature selection.

**Violin Plot** — The full density shape of the fraud class reveals whether fraud is concentrated in small amounts (card testing behavior) or large amounts (high-value theft), going beyond what a box plot alone can show.

---

## 🔮 Next Steps

- Apply SMOTE or class weighting to handle imbalance before model training
- Train classifiers: Logistic Regression, Random Forest, XGBoost, Isolation Forest
- Evaluate using Precision, Recall, F1-Score, AUC-ROC (not accuracy)
- Feature selection based on correlation with `Class`
- Threshold tuning to optimize fraud recall vs. false positive rate

---

## 🤝 Contributing

Pull requests are welcome. For major changes, open an issue first to discuss what you'd like to change.

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙏 Acknowledgements

- Dataset: [ULB Machine Learning Group — Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- Visualization guidance inspired by best practices in fraud analytics and imbalanced classification
