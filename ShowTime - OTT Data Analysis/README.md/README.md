# ShowTime OTT Platform: First-Day Viewership Predictive Modeling

An end-to-end predictive modeling and machine learning project using Linear Regression to determine what internal marketing levers and external timing factors drive first-day content viewership on an OTT platform.

---

## Project Overview & Business Problem
In a highly competitive Over-The-Top (OTT) streaming industry, maximizing immediate audience capture on day one of a release is vital to platform engagement and retention. Historically, ShowTime lacked a clear data-driven approach to estimate viewership spikes or distribute marketing assets effectively.

This project leverages historical data tracking internal performance indicators (trailers, ad campaigns) and external constraints (release seasons, competing live sports events) to build a robust predictive tool for upcoming platform releases.

---

## Technical Methodology & Pipeline
The project pipeline covers complete data science steps implemented in Python:
* **Data Preprocessing**: Handled missing values through imputation, eliminated duplicate entries, treated numerical outliers, and structured categorical attributes (`Genre`, `Day of Week`, `Season`) via encoding matrices.
* **Feature & Design Selection**: Used **Multiple Linear Regression** as the primary modeling choice due to its strong structural transparency and rapid business interpretability.
* **Assumption Validation**: Verified all basic Gauss-Markov criteria to ensure statistical model reliability:
  * **Linearity**: Visualized clear upward linear trends using scatter plots between target and features.
  * **Independence of Errors**: Satisfied the assumption with a **Durbin-Watson statistic of 2.038** (confirming zero serial correlation).
  * **Normality of Residuals**: Verified error distribution symmetry via a **Shapiro-Wilk p-value of 0.4379** (\(p > 0.05\)).
  * **Homoscedasticity**: Confirmed stable error variance via random residual spread plots.
  * **Multicollinearity Control**: Maintained stable coefficients with all **Variance Inflation Factor (VIF)** boundaries within acceptable industry limits.

---

##  Core Analysis & Key Business Insights

### 1. Viewership Dynamics (Target Distribution)
Exploratory Data Analysis (EDA) reveals that the first-day viewership metric is **right-skewed**. While the vast majority of media pieces achieve average, baseline traffic numbers, a small, highly profitable sub-tier drives massive outsized view counts.

### 2. Marketing Catalysts vs. Traffic
* **The Trailer Effect**: Pre-release trailer engagement exhibits the strongest relationship with first-day performance, maintaining a powerful correlation of **0.75**. Trailer views act as the single most critical early predictor of asset success.
* **Ad Reach & Platform Traffic**: Both advertisement impressions and active daily platform traffic display positive correlations, validating that paid marketing reach successfully brings users inside the platform funnel.

### 3. Structural Launch Timing & Competitor Friction
* **The Weekend Premium**: Weekend launches achieve significantly higher median view volumes than weekday attempts due to expanded consumer leisure windows.
* **Seasonal Elasticity**: Content performance scales strongly during holiday intervals and local festive periods.
* **Live Sports Crowding Out**: Releasing media streams simultaneously with major live external sports events results in massive viewership declines, as live sports divert finite user attention away from the platform.

---

##  Model Performance Evaluation
The finalized predictive engine demonstrates exceptional alignment and precision:
* **R-squared (\(R^2\)) Score: 0.77** — The configured parameters successfully account for **77%** of the underlying variance in first-day streaming performance.
* **Root Mean Squared Error (RMSE): 0.05** — The predictive deviation remains remarkably narrow, validating high model stability for forecasting upcoming release numbers.

---

##  Strategic Action Plan for ShowTime Management
* **Aggressive Pre-Release Engine**: Allocate additional marketing dollars toward amplifying trailer visibility and distribution, as high trailer interaction acts as the primary conversion pipeline.
* **Strategic Calendar Deployment**: Coordinate marquee and high-budget content releases to align directly with holiday seasons or weekend frames, avoiding scheduling overlaps with major national live sports broadcasts.
* **Ad Impression Optimization**: Optimize ad spending by matching investment models with target consumer clusters rather than applying flat budget limits.

---

##  Repository Structure
* **`Automobile_Analysis_Project/`** — Project 1: Portfolio consumer behavioral analysis engine.
* **`Inferential_Statistics_Coded_Project/`** — Project 2: Operational quality checking and hypothesis verification testing module.
* **`ShowTime_Predictive_Modeling_Project/`** (This folder)
  * `README.md` — Strategic outline, machine learning methodology, and core metrics.
  * `ShowTime_Regression_Notebook.ipynb` — Structured Python workbook covering preprocessing, data visualizations, VIF checks, and validation models.
  * `ShowTime_OTT_Data.csv` — Operational transaction records dataset.
