# All Life Bank: Credit Card Customer Segmentation (Unsupervised Learning)

An advanced unsupervised machine learning project executing customer segmentation pipelines to analyze credit card usage behaviors, financial limits, and omni-channel interaction preferences to personalize marketing and upgrade banking service delivery.

---

##  Project Overview & Business Problem
All Life Bank intends to optimize its credit card user footprint, reduce customer acquisition friction, customize retention offers, and eliminate service log bottlenecks. Applying one-size-fits-all product strategies frequently damages customer engagement and wastes cross-selling capital.

This project analyzes financial records spanning **660 banking customers across 7 continuous behavioral attributes**. Using mathematical clustering to classify the user base reveals distinct segments based on credit elasticity and branch vs. digital interaction trends, enabling data-backed operational planning.

---

##  Data Preprocessing & Unsupervised Feature Pipeline
The raw customer metrics were thoroughly preprocessed to ensure stable mathematical distance evaluations:
* **Identifier Refinement**: Removed non-behavioral system metrics (`Sl_No` and `Customer Key`) to prevent skewed geometric space calculations.
* **Data Verification**: Audited the dataset to confirm zero missing values and zero duplicate rows across the workspace.
* **Outlier Capping**: Identified continuous field skewness using the Interquartile Range (IQR) method (e.g., highly skewed `Avg_Credit_Limit` and `Total_visits_online`). Extreme limits were treated via mathematical capping rather than absolute row deletion to prevent information loss.
* **Advanced Feature Engineering**: Created multi-channel derived fields to isolate customer interaction patterns:
  * `Total_Interactions` = Total aggregate customer visits and phone logs across all bank channels.
  * `Digital_Interaction_Ratio` = Proportion of online engagement relative to total interaction velocity.
* **Z-Score Scaling**: Applied `StandardScaler` transformations to eliminate variable magnitude dominance, preventing large numeric columns like credit limits from overwhelming discrete visit and call counts.

---

##  Clustering Framework & Mathematical Evaluation
To ensure cluster stability, both parametric partitioning and distance-linkage methods were applied and cross-examined:
1. **K-Means Clustering**: Evaluated over a range of test `k` parameters.
   * **Elbow Curve**: Formulated inertia decay charts, locating a clear statistical inflection ("elbow") point around **3 clusters**.
   * **Silhouette Score**: Validated cluster cohesion and separation bounds, verifying that **k = 3** maximized the silhouette density score.
2. **Hierarchical Clustering**: Structured alternative distance maps using progressive linkage metrics and evaluated accuracy borders via **Cophenetic Correlation Coefficients** to verify geometric consistency against the raw distance matrix.

---

##  Identified Customer Segment Profiles
The final optimized clustering configuration mapped the portfolio cleanly into three actionable strategic groups:

###  Cluster 0: Low-Credit-Limit / Support-Heavy Customers
* **Behavioral Mix**: Low average credit limits, fewer active credit cards, and low in-branch or online visits. Conversely, this group generated the highest call volume with an average of **~6.9 phone interactions** per year.
* **Business Diagnostic**: This segment reflects unoptimized user onboarding or recurring system friction, forcing them to rely heavily on phone support to resolve account issues.

###  Cluster 1: Moderate-Credit-Limit / Branch-Traditionalists
* **Behavioral Mix**: Moderate credit limit thresholds and middle-tier product ownership. This group heavily favors physical infrastructure, leading the user base with an average of **~3.48 in-person branch visits** per year.
* **Business Diagnostic**: These customers rely on face-to-face relationship management and display a low affinity for independent digital banking apps.

###  Cluster 2: High-Value / Digitally Active Elites
* **Behavioral Mix**: High credit capacities (averaging over **100k+ credit limits**) and high account cross-holding (averaging **~8.7 credit cards**). They operate almost completely online, averaging **~8.18 digital platform visits** annually with minimal phone support needs.
* **Business Diagnostic**: This cluster represents the bank's most profitable, tech-savvy tier, showcasing an elite **Digital Interaction Ratio of ~83.7%**.

---

##  Corporate Action Plan for All Life Bank
* **Digital Onboarding & Training for Cluster 1**: Deploy branch-level relationship managers to actively guide traditional branch visitors through app installation and online portal setups, lowering brick-and-mortar branch overhead costs.
* **Friction Elimination for Cluster 0**: Audit the friction points triggering Cluster 0's heavy call volume. Introduce automated, proactive SMS notifications, clearer monthly statement layouts, and enhanced IVR self-service trees to reduce phone queue pressure.
* **Premium Cross-Selling for Cluster 2**: Roll out exclusive cross-selling campaigns to this high-value digital segment, offering high-tier product upgrades, wealth management advising, premium cashback ecosystems, and targeted luxury co-branded credit cards.

---
* **`Credit_Card_Segmentation_Project/`**
  * `README.md` — Strategic summary, preprocessing protocols, scaling records, and data cluster profiles.
  * `Unsupervised_Segmentation_Notebook.ipynb` — Structured Python file detailing PCA adjustments, Elbow plots, Dendrogram linkages, and cluster evaluation indices.
  * `all_life_bank_customers.csv` — Anonymized continuous demographic and interaction usage dataset.
