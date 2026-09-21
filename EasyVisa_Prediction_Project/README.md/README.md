# EasyVisa: Visa Application Certification Predictive Modeling

An advanced data modeling project utilizing robust ensemble machine learning classifiers, hyperparameter tuning, and class imbalance treatment techniques to automate and optimize the U.S. visa application screening process.

---

## Project Overview & Business Problem
The Office of Foreign Labor Certification (OFLC) experiences massive spikes in visa application forms annually, rendering manual evaluations highly resource-intensive and prone to processing backlogs. For organizations looking to bridge critical workforce gaps with skilled global talent, screening delays carry direct financial penalties.

This project uses historical visa evaluation attributes spanning **25,480 applicant rows and 12 distinct customer variables** to establish a reliable decision-support architecture. The engine segments applicants into high-probability approvals and targets borderline profiles needing immediate human oversight, minimizing operational strain while retaining absolute validation authority.

---

## Technical Preprocessing & Data Engineering
The raw transaction records featured structural noise and architectural issues that required standard production data treatments:
* **Anomaly Rectification**: Identified and handled invalid negative numbers within the `no_of_employees` column through median data distribution limits.
* **Feature Engineering**: Formulated a continuous time tracking metric, `company_age` (calculated via `2026 - yr_of_estab`), to capture operational longevity.
* **Multicollinearity Removal**: Dropped the original `yr_of_estab` baseline to eliminate a perfect negative correlation with the engineered age column, maximizing feature independence.
* **Data Leakage Defenses**: Enforced a strict stratified train/validation/test configuration split. Outlier boundary calculations, median continuous imputations, and mode categorical fills were fitted exclusively on the training matrix and subsequently broadcast across evaluation branches.
* **Class Imbalance Resolution**: Balanced the dataset's native class profile (roughly **66.8% Certified** vs. **33.2% Denied**) by evaluating:
  * Baseline data frameworks.
  * Synthetic Minority Over-sampling Technique (**SMOTE**).
  * Targeted undersampling matrices to ensure stable minority-class forecasting capability.

---

## Model Architecture & Ensemble Selection
To establish structural variance patterns, multiple complex classification architectures were constructed:
* **Base Learner**: Standard Decision Tree Classifier.
* **Bagging Ensembles**: Bagging Classifier, Random Forest, and Extra Trees.
* **Boosting Ensembles**: AdaBoost and Gradient Boosting Classifiers.

### Primary Success Optimization: F1-Score Focus
Because the underlying target parameter (`case_status`) displays a moderate class imbalance, **Validation F1-Score served as the primary optimization anchor** to balance high-precision constraints with maximum case discovery (Recall). 

---

## Evaluation Metrics Matrix (Original vs. Oversampled)
Below is a comparative breakdown of the top-performing ensemble algorithms across validation test frameworks:

| Model Algorithm | Train Accuracy | Validation Accuracy | Validation Precision | Validation Recall | Validation F1-Score | Validation ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Gradient Boosting (Original Data)** | `0.7571` | `0.7433` | `0.7735` | `0.8707` | **`0.8192`** | `0.7792` |
| **AdaBoost (Original Data)** | `0.7389` | `0.7297` | `0.7559` | `0.8794` | **`0.8130`** | `0.7629` |
| **Extra Trees (SMOTE Oversampled)** | `1.0000` | `0.7130` | `0.7619` | `0.8296` | **`0.7943`** | `0.7448` |
| **Random Forest (SMOTE Oversampled)** | `0.9999` | `0.7091` | `0.7768` | `0.7920` | **`0.7843`** | `0.7495` |

* **Final Selection**: The **Gradient Boosting Classifier** built on the original balanced data distribution provided the most stable generalized fit, yielding an **F1-Score of 0.82** and minimizing the training-to-validation generalization error gap.

---

## Core Exploratory & Structural Insights
* **The Education Premium**: Certification outcomes correlate heavily with academic qualifications. Doctorate applicants lead with an **87.2% certification rate**, followed by Master's holders at **78.6%**, whereas High School profiles drop down to a high-denial tier (**66% Denied**).
* **Prior Practical Experience**: Inbound records with verified corporate background logs (`has_job_experience`) secure a strong **74.5% approval rating**, showing clear validation preference over entry-level configurations.
* **Wage Structure Sensitivities**: Applications operating under annual salary structures (`unit_of_wage = Year`) demonstrate high stability. Conversely, hourly contract files (`unit_of_wage = Hour`) exhibit severe volatility, generating a massive **65.4% denial marker**.
* **Regional & Financial Benchmarks**: Intent locations distributed within the Midwest segment display strong approval profiles (**75.5% Certified**), heavily driven by higher baseline prevailing wage benchmarks across industrial sectors.

---

## Corporate Action Plan for EasyVisa Portfolio
* **Automated Decision Routing**: Implement the tuned Gradient Boosting pipeline as a triage layer to automatically flag high-probability approvals, allowing analysts to concentrate manual vetting pipelines onto grey-area applicant flags.
* **Structural Threshold Safeguards**: Set strict workflow constraints for hourly configuration files or high-school background inputs, automating immediate verification routines for these historically volatile brackets.
* **Dynamic Regional Planning**: Leverage regional approval imbalances to help client firms relocate workforce expansion initiatives toward target areas like the Midwest to maximize hiring speed.

---

## Portfolio Directory Index
* **`Automobile_Analysis_Project/`** — Project 1: Consumer behavioral distribution engine.
* **`Inferential_Statistics_Coded_Project/`** — Project 2: Industrial manufacturing process check module.
* **`ShowTime_Predictive_Modeling_Project/`** — Project 3: OTT streaming revenue linear regression tool.
* **`Hotel_Cancellation_Prediction_Project/`** — Project 4: Hospitality risk classification network.
* **`EasyVisa_Prediction_Project/`** (This folder)
  * `README.md` — Structural abstract, engineering parameters, and comparative ensemble arrays.
  * `EasyVisa_Ensemble_Tuning.ipynb` — Complete workbook tracking SMOTE transformations, structural trees, grid searches, and performance scorecards.
  * `easyvisa.csv` — Full analytical population dataset tracking corporate profiles and visa case history.
