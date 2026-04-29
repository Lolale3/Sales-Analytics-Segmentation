Sales Analytics & Customer Segmentation
Tools: Python · Pandas · XGBoost · Scikit-learn · Statsmodels · SHAP · Matplotlib · Seaborn · Plotly

Business Problem
A sales organization with $10.1M in revenue across 3 years (2003–2005) needed to understand:

Where revenue was coming from — by territory, product line, deal size, and customer
Why certain segments outperformed others
Who their most valuable customers were — and how to act on that
What sales would look like in the near term

This project tackles all four questions through exploratory analysis, predictive modeling, customer segmentation, and executive-ready reporting.

Project Structure
├── notebooks/
│   └── sales_analysis.ipynb        # Full analysis notebook
├── images/
│   ├── yearly_sales.jpg
│   ├── predicted_vs_actual.jpg
│   ├── shap_summary_plot.png
│   ├── shap_summary_features.png
│   ├── cluster.jpg
│   └── full_sales_dashboard.jpg
├── README.md
└── requirements.txt

Dataset
Source: Sample Sales Data — Kaggle
Download sales_data_sample.csv from Kaggle and place it in the root directory before running the notebook.

Analysis Modules
1. Exploratory Data Analysis

Yearly and monthly sales trends (2003–2005)
Territory performance: EMEA ($4.9M), NA ($3.8M), APAC, Japan
Product line revenue per unit: Classic Cars lead at $115.38/unit
Deal size distribution and revenue contribution
Rolling 3-quarter YoY growth by country
Correlation analysis: Price per unit (r=0.66) and quantity (r=0.55) as key revenue drivers

2. Sales Forecasting
Two models trained and evaluated on a time-based train/test split (last 5 months held out):
ModelMAERMSEHolt-Winters (Exponential Smoothing)——XGBoost Regressor——
Features used: Product line, deal size, price per unit, quantity ordered, MSRP
Model interpretation: SHAP values used to explain feature contributions to individual predictions
3. RFM-Based Customer Segmentation
K-Means clustering applied to Recency, Frequency, and Monetary value scores across 252 customers:
SegmentProfileCustomersAvg. MonetaryStrategy0 — Loyal High-Value BuyersRecent, frequent, high spend2$811,743Loyalty programs, premium upsell1 — Steady Mid-Tier CustomersLess recent, moderate spend76$113,495Reactivation, personalized campaigns2 — Low-Value Infrequent BuyersPrice-sensitive, small deals91$115,260Bundle offers, discount promotions3 — Inactive Big-Ticket BuyersChurned, historically high spend83$111,599Win-back campaigns, exclusive offers
4. Revenue Uplift Quantification
SegmentStrategyEstimated Revenue ImpactLoyal High-Value Buyers10% upsell uplift$162,000Steady Mid-Tier Customers15% reactivation uplift$1,290,000Low-Value Infrequent Buyers7% bundle/promo uplift$735,000Inactive Big-Ticket Buyers20% reactivation × 10% upsell$185,718Total$2.37M+
5. Executive Dashboard
Multi-panel dashboard covering:

KPI summary (total sales, orders, customers, churn rate)
Month-over-Month revenue growth rate
Monthly sales trend
Top 10 countries by revenue
Product line performance by deal size
Top 5 customers by total sales
Quarterly sales by product line
Sales distribution by deal size


Key Findings

EMEA drives 49% of total revenue with the highest average order value (~$3,539)
Classic Cars deliver the highest revenue per unit at $115.38 — premium positioning opportunity
Price per unit is the strongest sales driver (r=0.66 correlation with revenue) — value-based pricing outperforms volume discounting
2 customers account for the highest-value segment (Segment 0, ~$1.62M combined) — retention of this group is critical
Segment 1 represents the largest revenue opportunity — $1.29M potential uplift through reactivation of 76 mid-tier customers
Japan is a niche high-value market with the highest average order value ($3,761) despite lowest total sales — opportunity for premium product focus


Business Recommendations

Double down on EMEA and NA — these territories drive the majority of revenue and show strong average order values
Prioritize Classic Cars in marketing — highest revenue per unit, strongest appeal to high-value segments
Launch targeted reactivation campaigns for Segment 1 — largest addressable revenue opportunity at $1.29M
Protect Segment 0 — just 2 customers, but $1.62M in combined value; personalized retention is non-negotiable
Use value-based pricing — price per unit drives revenue more than order volume; protect margins over volume discounts


How to Run
bash# Install dependencies
pip install -r requirements.txt

# Download dataset from Kaggle and place in root directory
# https://www.kaggle.com/datasets/kyanyoga/sample-sales-data

# Launch notebook
jupyter notebook notebooks/sales_analysis.ipynb
