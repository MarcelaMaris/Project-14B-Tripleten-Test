# 🧪 A/B Testing — Recommender System Experiment

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow)
![Statistics](https://img.shields.io/badge/Statistics-Z%20Test-green)
![License](https://img.shields.io/badge/License-MIT-green)

## 📌 Project Overview
This project was developed as part of the **Data Analytics Bootcamp at [TripleTen](https://tripleten.com)**.  
It analyzes the results of an **A/B experiment** conducted by an international online store to measure the impact of a **new recommender system** on user conversion behavior across different funnel stages.

Using **Python**, **Pandas**, and statistical hypothesis testing, the analysis focuses on **data validation**, **conversion funnel construction**, and **Z-tests** to evaluate whether the new system led to statistically significant improvements in user conversion rates.


💻 **Repository:** [https://github.com/MarcelaMaris/AB-Testing-Recommender-System-Experiment](https://github.com/MarcelaMaris/AB-Testing-Recommender-System-Experiment)

---

## 🎯 Objectives

- Validate and clean A/B testing data (new users, events, participants).  
- Build and analyze user conversion funnels by group (A vs. B).  
- Investigate behavioral patterns through EDA.  
- Apply **proportion Z-tests** to evaluate statistical significance of conversion differences.  
- Provide insights and recommendations regarding the new recommendation system.

---

## 🧭 Analysis Overview

- **Data inspection & cleaning**  
  Checked structure, types, duplicates, and missing values across four datasets.  

- **Conversion funnel construction**  
  Built both **simple** (unique counts per user) and **time-sequenced** funnels to accurately track user behavior.

- **EDA & behavioral patterns**  
  Examined event distributions per user and over time to validate experiment consistency.

- **Hypothesis testing**  
  Performed one-tailed Z-tests for three funnel steps:
  - Product view → Cart addition  
  - Cart addition → Purchase  
  - Product view → Purchase (full funnel)

---

## 📌 Key Insights

- The **B group** showed slightly higher conversion from product view to cart (24% vs. 23%),  
  but the **A group** performed marginally better in final purchase conversion.  
- All p-values were **> 0.05**, indicating no statistically significant differences.  
- Both groups showed **parallel event patterns over time**, confirming experiment consistency.  
- The largest drop occurred in the **cart → purchase step**, highlighting a conversion bottleneck.

---

## 📝 Recommendations

- **Investigate checkout funnel** — payment options, pricing strategies, or UX issues may explain the bottleneck.  
- **Run targeted experiments** focusing on the cart-to-purchase step to boost final conversions.  
- Consider further segmenting users (e.g., by device or acquisition channel) for deeper behavioral insights.

---

## 🛠️ Tech Stack

- **Data Analysis:** Python, Pandas, NumPy  
- **Statistical Testing:** statsmodels (Z-test)  
- **Visualization:** Matplotlib, Plotly, Jupyter Notebook

---

## 💡 Business Impact

- Provided **clear evaluation** of the recommender system’s effectiveness.  
- Identified **conversion bottlenecks** and next steps for optimization.  
- Demonstrated **robust A/B testing methodology** suitable for data-driven decision-making.
