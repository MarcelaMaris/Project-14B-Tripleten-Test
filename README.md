<p align="center">
  <img src="cover_ABtest.png" width="100%" alt="E-Commerce Analytics Dashboard cover">
</p>


## <img src="icons/testingAB.png" width="50">  &nbsp;&nbsp;Recommender System A/B Test — Conversion Funnel & Statistical Validation
<br>

![Python](https://img.shields.io/badge/Python-3.10%2B-0A3756?style=flat&logo=python&logoColor=F5F7FA&labelColor=E8AA3A)
![Pandas](https://img.shields.io/badge/Pandas-lib-0A3756?style=flat&logo=pandas&logoColor=F5F7FA&labelColor=E8AA3A)
![NumPy](https://img.shields.io/badge/NumPy-lib-0A3756?style=flat&logo=numpy&logoColor=F5F7FA&labelColor=E8AA3A)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Z%20Test-0A3756?style=flat&logo=python&logoColor=F5F7FA&labelColor=E8AA3A)
![Funnel](https://img.shields.io/badge/Analysis-Conversion%20Funnel-0A3756?style=flat&logo=googleanalytics&logoColor=F5F7FA&labelColor=E8AA3A)

> This project analyses an **A/B experiment** for an international e-commerce platform testing an  
> **improved recommendation system** (Group B) against the current experience (Group A).
>
> The objective is to evaluate whether the new recommender produces at least a **10% uplift** across key funnel stages  
> within **14 days after sign-up**:
>
> **Product Page View → Add to Cart → Purchase**
>
> The analysis combines **data validation**, **conversion funnel modelling (sequence-aware)**, and  
> **statistical hypothesis testing (one-tailed proportion Z-tests)** to support a clear product decision:
> **should the new recommender be rolled out?**

💻 **Repository:** https://github.com/MarcelaMaris/AB-Testing-Recommender-System-Experiment

---

## <img src="icons/objectives.png" width="30">  &nbsp;&nbsp;Objectives

- Validate the integrity of A/B experiment data (users, events, participants, marketing calendar).
- Build a **conversion funnel** for Groups A and B across three core stages:
  - `product_page` → `product_cart` → `purchase`
- Ensure funnel steps follow a **logical event sequence** per user (time-ordered funnel).
- Quantify conversion differences between groups at each stage.
- Run **one-tailed proportion Z-tests** to test whether **Group B outperforms Group A**.
- Translate findings into **product recommendations** and next steps.

---

## <img src="icons/features.png" width="30">  &nbsp;&nbsp;Key Analyses & Features

- **Data Preparation & Quality Checks**
  - Loaded four datasets: marketing calendar, new users, events, and A/B participants.
  - Verified schema, missing values, duplicates, and data readiness.
  - Converted all date fields to `datetime` to support filtering and joins.

- **Experiment Consistency Validation**
  - Checked overlap between events and participants to ensure the analysis is restricted to test users.
  - Compared event volume distribution per user between groups to detect behavioural imbalance.
  - Evaluated daily event trends to confirm groups ran in parallel over time.

- **Conversion Funnel (Two Approaches)**
  - **Unique-user funnel:** one count per user per event stage.
  - **Time-ordered funnel (primary):** enforced the logical action order per user using first event timestamps:
    `product_page → product_cart → purchase`
  - Adjusted time comparisons from `>` to `>=` to handle identical timestamps without excluding valid behaviour.

- **Hypothesis Testing**
  - Applied **one-tailed Z-tests for proportions** at three funnel steps:
    1. View → Cart  
    2. Cart → Purchase  
    3. View → Purchase (full conversion)

---

## <img src="icons/dataset.png" width="30">  &nbsp;&nbsp;Dataset

**Tables used**
- `ab_project_marketing_events_us.csv` — marketing calendar (context for timeline)
- `final_ab_new_users_upd_us.csv` — user sign-up attributes (date, region, device)
- `final_ab_events_upd_us.csv` — event logs (timestamped user actions)
- `final_ab_participants_upd_us.csv` — A/B test allocation (Group A/B)

⚠️ **Data note**  
`details` contains many nulls by design, as it applies only to purchase-related events (e.g., revenue).

---

## <img src="icons/funnel.png" width="30">  &nbsp;&nbsp;Conversion Funnel

The funnel focuses on three behavioural milestones:

- `product_page` — product page views  
- `product_cart` — add-to-cart actions  
- `purchase` — completed purchases  

The **primary funnel** is the **time-ordered funnel**, where each step is only counted if:
- the event exists for the user, and
- its timestamp occurs **after or at the same time** as the prior step.

This ensures the funnel represents a **valid user journey**, not just event presence.

---

## <img src="icons/conclusions.png" width="30">  &nbsp;&nbsp;Key Results

### Funnel performance (time-ordered)
- **View → Cart**
  - Group B conversion is **slightly higher** than Group A (≈ 24% vs. 23%).
- **Cart → Purchase**
  - Group A performs **slightly better**, and both groups show a strong drop at this step.
- **Full conversion (View → Purchase)**
  - No meaningful uplift for Group B.

### Statistical testing (one-tailed Z-test: B > A)
- **View → Cart:** p = **0.0996** → not significant at 0.05  
- **Cart → Purchase:** p = **0.8201** → not significant  
- **View → Purchase:** p = **0.6823** → not significant  

✅ **Conclusion:** There is **no statistically significant evidence** that the new recommender (B) improves conversion at any funnel stage.

---

## <img src="icons/impact.png" width="30">  &nbsp;&nbsp;Business Impact

- Delivered a **decision-ready evaluation** of the recommender system test.
- Prevented a potentially costly rollout based on **non-significant uplifts**.
- Highlighted a critical bottleneck at **cart → purchase**, suggesting the main revenue lever is downstream of recommendations.

---

## <img src="icons/recommendations.png" width="30">  &nbsp;&nbsp;Recommendations

- **Investigate the cart → purchase bottleneck**  
  Review checkout UX, pricing, shipping, and payment methods to reduce final-stage drop-off.

- **Run follow-up experiments focused on checkout conversion**  
  A recommender may improve engagement, but revenue impact likely depends on the purchase flow.

- **Segment analysis for deeper insight (next iteration)**  
  Compare uplift by **device**, **region**, acquisition channel, or cohort (new vs. returning) to detect heterogeneous effects.

- **Add guardrails to experiment design**  
  Pre-define primary metric(s), minimum detectable effect, and ensure event tracking consistency (especially timestamps).

---

## <img src="icons/techstack.png" width="30">  &nbsp;&nbsp;Tech Stack

- **Languages & Libraries:** Python (3.10), Pandas, NumPy  
- **Statistical Testing:** statsmodels (proportions Z-test)  
- **Visualisation:** Plotly (funnel charts), Matplotlib (time series)  
- **Environment:** Jupyter Notebook  
- **Version Control:** Git & GitHub  

---

<p align="center">
  <sub>📊 Designed & developed by <b>Marcela Maris</b> — Data Analytics Portfolio</sub><br>
  <sub><i>A/B Testing • Conversion Funnel • Product Analytics</i></sub>
</p>





