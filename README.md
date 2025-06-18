# Predicting-Customer-Churn-and-Price-Sensitivity-Impact-in-Power-Utilities

## 1. Project Background
This report analyzes the impact of price sensitivity on customer churn in a power utility company and develops a predictive model for churn behavior. The goal is to provide data-driven recommendations for customer retention strategies.

---

## 2. Data Overview
### Datasets
- **client_data.csv**: Contains customer characteristics (e.g., income level, subscription type) and churn status (`churn`).
- **price_data.csv**: Includes price-related variables (e.g., forecasted electricity prices, discounts, profit margins).

### Key Variables
- **Price Sensitivity Metric**: Derived from variables like forecasted prices, discounts, and consumption patterns.
- **Target Variable**: `churn` (binary indicator of customer attrition).

---

## 3. Methodology
### 3.1 Price Sensitivity and Churn Analysis
- **Approach**:
  - Categorized price sensitivity into Low, Medium, and High tiers.
  - Used group statistics and visualizations (bar plots, heatmaps) to analyze churn rate differences.
  - Calculated Pearson correlation coefficients to assess linear relationships.
- **Tools**: `pandas`, `seaborn`, `matplotlib`.

### 3.2 Feature Engineering
- **Constructed Features**:
  1. **Price Difference Features**: e.g., monthly off-peak price variations (`offpeak_diff_dec_january_energy`).
  2. **Customer Loyalty Features**: e.g., active months (`months_activ`), contract remaining months (`months_to_end`).
  3. **Data Transformations**: One-hot encoding for categorical variables, log transforms for skewed numerical features.
- **Purpose**: Enhance model capability to capture price fluctuations and customer behavior.

### 3.3 Predictive Modeling
- **Model**: Random Forest Classifier (`RandomForestClassifier`).
- **Evaluation Metrics**: Accuracy, Precision, Recall, Confusion Matrix.
- **Feature Importance Analysis**: Extracted via model's built-in methods.

---

## 4. Key Findings
### 4.1 Price Sensitivity and Churn
- **High-sensitivity customers churn significantly more**:
  - Churn rate for High-sensitivity: ~**50%**, Low-sensitivity: <**20%**.
- **Price sensitivity is a key driver**, but not the sole factor (interacts with other variables).

### 4.2 Model Performance
- **Metrics**:
  - Accuracy: **90.36%**, Precision: **81.82%**, Recall: **4.92%**.
  - Low recall indicates limited ability to identify actual churn cases.
- **Top Predictive Features**:
  1. **Net Margin (`net_margin`)**
  2. **12-month Consumption (`cons_12m`)**
  3. **Power Subscription Margin (`margin_net_pow_ele`)**
  4. **Active Months (`months_activ`)**

### 4.3 Additional Insights
- **Customer Loyalty**: `tenure` negatively correlates with churn.
- **Price Volatility**: Off-peak price differences weakly contribute to churn prediction.

---

## 5. Conclusions & Recommendations
### 5.1 Conclusions
- Price sensitivity is influential, but **net margin and consumption patterns** are stronger predictors.
- The model achieves high overall accuracy but requires improvements in recall for churn detection.

### 5.2 Business Recommendations
1. **Targeted Discounts**:
   - Offer personalized discounts to high-value (high net margin) at-risk customers.
2. **Loyalty Programs**:
   - Incentivize long-term contracts or reward systems to increase `tenure`.
3. **Price Monitoring**:
   - Track peak/off-peak price differentials for high-sensitivity segments.

### 5.3 Next Steps
- **Feature Engineering**: Incorporate behavioral data (e.g., complaints, service usage frequency).
- **Model Optimization**: Experiment with ensemble methods (e.g., XGBoost) or class weighting to improve recall.

---

## 6. Appendix
### Code Implementation
- **Data Preprocessing**: Handling missing values, data type conversions (`pandas`).
- **Visualizations**: Heatmaps, bar plots (`seaborn`).
- **Modeling**: Random Forest training/evaluation (`sklearn`).

### Data Files
- Cleaned data: `clean_data_after_eda.csv`
- Engineered features: `data_for_predictions.csv`
