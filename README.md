# My-GL-Projects
# My-GL-Projects
# Austo Automobiles: Marketing Campaign Effectiveness Analysis

A comprehensive data analytics and business strategy project designed to uncover how customer demographics, income brackets, and financial factors influence vehicle preferences and purchase decisions. 

---

## Executive Summary & Business Problem
Austo Automobiles operates in a highly competitive market offering SUVs, Sedans, and Hatchbacks. Historically, the company lacked an analytical understanding of customer purchasing behavior, resulting in baseline, non-optimized marketing, pricing, and targeting strategies. 

This project explores a customer-level dataset containing **1,581 records and 14 strategic features** to decode the underlying drivers behind premium car purchases, calculate segment-specific demand, and unlock revenue optimization strategies.

---

## Technical Methodology & Data Engineering
Before running the business logic, the raw dataset was processed using professional Python data treatment techniques:
* **Missing Value Imputation**: Addressed gaps by applying `Mode` imputation for categorical attributes (`Gender`) and `Median` imputation for skewed numerical variables (`Partner_salary`).
* **Feature Engineering**: Recalculated dynamic household metrics via `Total_salary = Salary + Partner_salary` to isolate true household buying power.
* **Text Normalization**: Cleaned and unified typographical errors in categorical labels (e.g., standardizing structural typos in `Gender`).
* **Outlier Capping**: Utilized the **Interquartile Range (IQR) Method** to isolate high-potential outliers in `Total_salary` and `Price`, applying robust upper/lower bound capping to stabilize metrics without deleting valuable premium customer profiles.

---

## Key Data Insights

### 1. Gender Dynamics & Body Style Preferences
* **Men** exhibit a powerful structural preference for **SUVs**, prioritizing practical, value-oriented, and premium features.
* **Women** demonstrate a higher affinity for **Sedans and Hatchbacks**, showing value-driven, comfort-oriented, and price-sensitive shopping habits.
* Male buyers feature a significantly higher average spending cap on vehicle purchases, predominantly driven by these high-end SUV configurations.

### 2. Income vs. Life Stage Elasticity
* While a distinct positive relationship exists between `Salary` and `Price` (showing that income sets a baseline budget), income alone does not predict car type. 
* Correlation maps prove that **Age/Life Stage** serves as a stronger statistical predictor of total vehicle spend than absolute single-income salary.
* Budget-conscious or mid-income salaried professionals lean heavily toward **Sedans**. However, as income parameters increase, demand dynamically pivots toward premium **SUVs**.

### 3. Credit & Dual-Income Catalysts
* Access to capital drastically reduces price sensitivity; individuals utilizing **Personal Loans** push their budgets to acquire significantly higher-priced tiers.
* Dual-income households (`Partner_working`) create a highly lucrative cluster, showcasing massive combined purchasing power and a much higher frequency of premium SUV adoption.

---

## Strategic Action Plan for Austo Automobiles
* **Targeted SUV Deployments**: Launch specialized campaigns exclusively positioning premium SUVs to salaried male professionals and high-earning dual-income households.
* **Credit-Linked Conversion**: Reduce upfront price sensitivity barrier by embedding flexible vehicle financing packages and structured personal loan offerings right alongside premium car configurations.
* **Age-Segmented Communications**: Restructure digital marketing channels to rely heavily on age-based demographics alongside baseline financial indicators to personalize copy.

---

## Repository Structure
* **`Module_1_Project.ipynb`**: Interactive Jupyter Notebook containing Exploratory Data Analysis (EDA), KDE distribution charts, correlation heatmaps, and regressions.
* **`austo_automobile.csv`**: Target clean demographic and transaction asset file.
* **`Business_Report.pdf`**: C-suite ready strategic report detailing data explanations and deep-dive actionable metrics.
