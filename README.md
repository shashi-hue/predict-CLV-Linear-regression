# Customer Lifetime Value (CLV) Prediction 

A machine learning project that predicts how much money customers will spend in the future based on their past shopping behavior.

## What This Project Does

This project analyzes customer purchase history to predict their **Customer Lifetime Value (CLV)** - essentially answering the question: *"How much will this customer spend with us in the next 90 days?"*

Understanding CLV helps businesses:
- Identify their most valuable customers
- Allocate marketing budgets more effectively
- Improve customer retention strategies
- Make data-driven decisions about customer acquisition

## Dataset Overview

We used the **Online Retail II dataset** from UCI, which contains:
- **5,881 unique customers** after cleaning
- Purchase transactions from an online retail store
- Features like invoice dates, quantities, prices, and product codes
- Data split: Historical data for training + last 90 days for CLV calculation

## How It Works

### 1. Data Cleaning
- Removed orders without Customer IDs (can't track CLV without knowing the customer!)
- Filtered out cancelled orders (invoices starting with 'C')
- Converted dates and calculated total order amounts

### 2. Smart Feature Engineering
We created meaningful features that capture customer behavior:
- **Customer age**: How long they've been shopping with us
- **Purchase frequency**: How often they buy per month
- **Product diversity**: Variety of products they purchase
- **Recency**: Days since their last purchase
- **One-time buyer flag**: Whether they've only bought once

### 3. Handling the CLV Challenge
CLV data is naturally skewed - most customers spend little, but a few spend A LOT. We used log transformation to make the data more manageable for our model.

### 4. Model Selection
We started with **Linear Regression** because it's:
- Easy to interpret (we can see which factors matter most)
- Quick to train and validate
- Provides a solid baseline for comparison

## Key Findings

### Model Performance
- **R² Score**: 0.236 (explains 23.6% of variance)
- **RMSE**: £1.42 (average prediction error)
- **Strong average accuracy**: Predicted mean CLV very close to actual mean

### Most Important Factors for CLV
1. **Unique invoices** - How many separate orders they've made
2. **Total quantity** - How much they've bought overall
3. **Days since last purchase** - Recent customers tend to spend more
4. **Average days between purchases** - Shopping frequency patterns

### Customer Insights
- **64.2% are one-time buyers** - huge retention opportunity!
- Average customer relationship: 200+ days
- CLV ranges from £0 to £500+ with most customers under £50

## Limitations & Next Steps

### Current Limitations
- Linear regression struggles with extreme CLV values (very high or very low spenders)
- CLV prediction is inherently non-linear - customer behavior is complex!
- Model explains only ~24% of variance, leaving room for improvement

### Future Improvements
1. **Try non-linear models** like XGBoost or Random Forest
2. **Customer segmentation** - separate models for different customer types
3. **Time-based features** - seasonal patterns, holidays, etc.
4. **External data** - demographics, marketing campaign exposure
5. **Ensemble methods** - combining multiple models

## Key Takeaways

1. **Start simple**: Linear regression provides interpretable insights even if not perfect
2. **Feature engineering matters**: Smart features often beat complex models
3. **Customer behavior is complex**: Non-linear relationships require advanced modeling
4. **Business value**: Even imperfect models provide actionable insights for customer strategy

## Business Applications

This model can help businesses:
- **Prioritize customer service** for high-CLV customers
- **Design targeted marketing campaigns** based on predicted value
- **Set acquisition budgets** by understanding customer worth
- **Identify at-risk customers** (those with declining CLV predictions)

---

*While linear regression offers a strong starting point and interpretable results, CLV prediction is inherently non-linear due to highly skewed customer behavior. Future improvements could include non-linear models (e.g., XGBoost) and segmentation strategies to better capture extreme customer behaviors.*
