# 🧪 A/B Testing in Databricks — EDA + Statistical Significance

## 📖 What is A/B Testing?
A/B testing is an experimental method to compare two versions of something — **Variant A** (control) and **Variant B** (treatment) — to see which performs better for a specific metric.

In this case, we’re testing **user engagement and monetization metrics** for two variants.

---

## 📊 Metrics in Our Test

- **Impressions**: Number of times an item/ad was shown  
- **Clicks**: Number of times it was clicked  
- **Orders**: Purchases made after clicking  
- **Revenue**: Money earned from orders  

From these, we calculate:

- **Click-Through Rate (CTR)** = `Clicks / Impressions × 100`
- **Conversion Rate** = `Orders / Clicks × 100`
- **Average Revenue per User (ARPU)** = `Revenue / Number of Users`

---

## 📦 Synthetic Experiment Scenario

**Experiment**: Testing a new ad ranking model on the Instacart homepage.  

- **Variant A (Control)** → current ranking algorithm  
- **Variant B (Treatment)** → new ranking algorithm  

**Goal**: Increase CTR and conversion rate, while maintaining or improving revenue.

---

## 📁 Dataset Columns

| Column       | Type    | Description                                       |
|--------------|---------|---------------------------------------------------|
| user_id      | int     | Unique shopper ID                                 |
| variant      | string  | 'A' (control) or 'B' (treatment)                   |
| impressions  | int     | Number of ads shown                               |
| clicks       | int     | Number of ads clicked                             |
| orders       | int     | Orders placed after clicking                      |
| revenue      | float   | Total revenue from orders                         |

---

## 🔬 Why Statistical Testing?
Raw numbers can be misleading — differences might be due to **chance**.  

We use **p-values** to test statistical significance:
- **p < 0.05** → Significant (unlikely to be random)
- **p ≥ 0.05** → Not significant (could be random noise)

**Tests Used:**
- CTR% → Chi-square test  
- Conversion% → Chi-square test  
- Revenue/User → t-test  

---

## 🚀 Project Highlights
- Data cleaning to remove invalid metrics (e.g., clicks > impressions)
- Metric calculation in Databricks SQL
- Statistical significance testing in Python (Chi-square, t-test)
- Visualization using Matplotlib + Seaborn
- Clear documentation of A/B testing methodology

---

## 📊 Results Summary

| Metric            | Variant A | Variant B | p-value | Significant? |
|-------------------|-----------|-----------|---------|--------------|
| CTR%              | 8.15%     | 9.67%     | 0.0000  | ✅ Yes       |
| Conversion%       | 11.81%    | 12.71%    | 0.1565  | ❌ No        |
| Avg Revenue/User  | $218.49   | $280.69   | 0.0000  | ✅ Yes       |

---

## 📈 Visual Results

### CTR Comparison
![CTR Comparison](images/ctr_comparision.png)

### Revenue per User Comparison
![Conversion Rate Comparison](images/ctr_comparision.png)

### Conversion Rate Comparison
![Revenue Comparison](images/conversion_rate_comparision.png)

---

## ✅ Conclusion
Variant B has a **significantly higher CTR and ARPU**.  
Conversion rate difference is **not statistically significant**.  

**Recommendation:** Roll out Variant B and monitor long-term performance.

---

## 🛠 Tech Stack
- **Databricks SQL** → Data preparation & aggregation
- **Python (Pandas, Seaborn, SciPy)** → Statistical testing & visualization
- **Matplotlib** → Charts

---

## 📂 Repo Structure
```
ab-testing-databricks/
├── notebook/
│ └── ab_testing_databricks.ipynb
├── images/
│ ├── ctr_comparison.png
│ ├── revenue_comparison.png
│ └── conversion_rate_comparison.png
├── data/ # optional
│ └── ab_test_sample.csv
└── README.md
```
---

## 📄 Author
**Rehan Chaudhry**  
[GitHub Portfolio](https://github.com/rehansc)  
[LinkedIn](https://www.linkedin.com/in/rehanchaudhry/)
