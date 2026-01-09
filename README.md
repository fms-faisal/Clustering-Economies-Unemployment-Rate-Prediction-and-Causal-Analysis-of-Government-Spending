# Clustering Economies: Unemployment Rate Prediction and the Role of Government Spending

[Google colab](https://colab.research.google.com/github/fms-faisal/Clustering-Economies-Unemployment-Rate-Prediction-and-Causal-Analysis-of-Government-Spending/blob/main/Clustering%20Economies_Unemployment%20Rate%20Prediction%20and%20Causal%20Analysis%20of%20Government%20Spending.ipynb) | [GitHub](https://github.com/fms-faisal/Clustering-Economies-Unemployment-Rate-Prediction-and-Causal-Analysis-of-Government-Spending)

This project analyzes global economic indicators to predict unemployment rates and evaluates the causal impact of government spending on unemployment across different economic clusters. The study utilizes data from the **IMF World Economic Outlook (2015–2024)**.

The research approach is threefold:
1.  **Prediction**: Benchmarking regression models to predict unemployment rates.
2.  **Clustering**: Grouping countries into Low, Medium, and High unemployment categories using K-Means.
3.  **Causal Inference**: Estimating the effect of government spending on unemployment for each cluster using Causal Analysis (DoWhy).

---

## 📂 Included Files

| File Name | Description |
|-----------|-------------|
| `Clustering Economies_... .ipynb` | Main notebook containing data preprocessing, model training, clustering, and causal analysis. |
| `dataset_2024...IMF.RES_WEO...csv` | Raw dataset obtained from the IMF World Economic Outlook database. |
| `transposed_dataset.csv` | Transposed version of the raw data, converting year-columns into rows. |
| `removed_unwanted_..._cleaned_01.csv` | Intermediate data file with columns having >50% missing values removed. |
| `unemployment_rate_dataset_cleaned.csv` | Final cleaned dataset used for modeling (948 rows × 40 columns). |
| `top_10_models.csv` | CSV export of the performance metrics for the top 10 regression models. |

---

## 📊 Phase 1: Unemployment Rate Prediction

We evaluated over 20 regression models, including Ensemble methods (Voting, Stacking) and Tree-based models. **Extra Trees** performed best, achieving an $R^2$ of **93.34%** in its initial configuration.

### Model Performance Metrics
The heatmap below visualizes the performance of the top models. While hyperparameter tuning was attempted, the default **Extra Trees** model outperformed the optimized version.

| Model | $R^2$ Score | MAE | MSE | RMSE |
|-------|----------|-----|-----|------|
| **Extra Trees (Initial)** | **0.9334** | **0.8631** | **2.643** | **1.4047** |
| Extra Trees (Optimized) | 0.911 | 1.129 | 2.644 | 1.626 |
| CatBoost | 0.901 | 1.130 | 2.919 | 1.709 |
| Stacking Regressor | 0.900 | 1.144 | 2.955 | 1.719 |
| Voting Regressor | 0.874 | 1.350 | 3.736 | 1.933 |
| XGBoost | 0.854 | 1.419 | 4.313 | 2.077 |

**Visual Examples**

| Model Performance Heatmap | Top 10 Models by $R^2$ Score |
| :---: | :---: |
| <img src="images/Model Performance Heatmap.png" width="100%" alt="Model Performance Heatmap" /> | <img src="images/Top 10 Models Chart.png" width="100%" alt="Top 10 Models Chart" /> |

---

## 🌍 Phase 2: Clustering Countries by Unemployment

To understand economic patterns, we applied **K-Means Clustering** to group countries into three distinct categories based on their unemployment rates.

| Cluster | Category | Center (Unemployment Rate) | Count | Example Countries |
|:-------:|----------|----------------------------|-------|-------------------|
| **0** | **Low** | 0.563 | 600 | Aruba, Switzerland |
| **1** | **Medium** | 0.557 | 284 | Kosovo  |
| **2** | **High** | 2.810 | 64 | South Africa, Sudan |

**Visual Examples**

| Clustering of Countries | Distribution by Category |
| :---: | :---: |
| <img src="images/Clustering of Countries.png" width="100%" alt="Clustering Scatter Plot" /> | <img src="images/Distribution by Category.png" width="100%" alt="Unemployment Distribution Boxplot" /> |

---

## 📉 Phase 3: Causal Analysis of Government Spending

We analyzed the causal impact of **Government Spending** (treatment) on the **Unemployment Rate** (outcome), controlling for Savings Rate, Population, and GDP Per Capita.

**Key Finding:** Government spending is most effective in reducing unemployment in countries with **Medium** unemployment rates. It has a minimal impact in countries where unemployment is already low.

| Employment Category | Causal Effect Estimate | Interpretation |
|---------------------|------------------------|----------------|
| **Medium** | **0.0357** | **Strongest Positive Impact**  |
| High | 0.0295 | Moderate Impact  |
| Low | 0.0120 | Weakest Impact  |

**Visual Example**

| Causal Effect Estimates by Category |
| :---: |
| <img src="images/Causal Effect Estimates by Category.png" width="60%" alt="Causal Effect Estimates Bar Chart" /> |

---

## 🔗 Dataset Source

**Source**: IMF World Economic Outlook Database (2015–2024)  
**Content**: Economic indicators for 195 countries including GDP, government spending, and unemployment rates.

---

## 🚀 How to Run in Google Colab

1. Open [Google Colab](https://colab.research.google.com/)
2. Select "GitHub" tab
3. Paste: `https://github.com/fms-faisal/Clustering-Economies-Unemployment-Rate-Prediction-and-Causal-Analysis-of-Government-Spending.git`
4. Select the notebook `Clustering Economies... .ipynb` to open.

**Or clone manually**:
```bash
!git clone [https://github.com/fms-faisal/Clustering-Economies-Unemployment-Rate-Prediction-and-Causal-Analysis-of-Government-Spending.git](https://github.com/fms-faisal/Clustering-Economies-Unemployment-Rate-Prediction-and-Causal-Analysis-of-Government-Spending.git)
%cd Clustering-Economies-Unemployment-Rate-Prediction-and-Causal-Analysis-of-Government-Spending
