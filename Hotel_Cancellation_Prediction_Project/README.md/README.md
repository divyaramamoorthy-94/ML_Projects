# INN Hotels Group: Machine Learning Solution for Booking Cancellation Prediction

An end-to-end predictive classification and machine learning optimization project designed to forecast hotel booking cancellations, reduce revenue leakage, and stabilize room occupancy planning.

---

##  Project Overview & Business Problem
INN Hotels Group faces severe financial and operational uncertainty due to sudden booking cancellations and no-shows. Unanticipated room vacancies close to arrival dates result in missed revenue, lower room utilization, and wasted staff distribution efforts. 

Exploratory analysis revealed an impactful **historical baseline cancellation rate of 32.8%** across the group's properties—meaning roughly one out of every three reservations fails to materialize. This project establishes an automated, data-driven machine learning engine to identify high-risk reservations in advance.

---

##  Technical Methodology & Pipeline
The predictive infrastructure evaluates a robust dataset containing **36,275 rows and 19 operational features**:
* **Data Preprocessing & Quality Checks**: Verified zero missing values across the system. Applied statistical capping via the Interquartile Range (IQR) method to stabilize numerical outliers (`lead_time`, `avg_price_per_room`) without removing premium customer records.
* **Feature Engineering**: Formulated behavioral domain features to capture true customer intent:
  * `total_nights` = `no_of_weekend_nights` + `no_of_week_nights`
  * `total_guests` = `no_of_adults` + `no_of_children`
  * `total_previous_bookings` = `no_of_previous_cancellations` + `no_of_previous_bookings_not_canceled`
* **Encoding & Scaling**: Processed high-cardinality features using one-hot encoding matrices, transformed the target variable to binary formats, and standardized features via `StandardScaler`.
* **Model Implementation**: Formulated cross-validated comparative frameworks:
  * **Logistic Regression (`statsmodels`)**: Configured to isolate linear feature dependencies, remove redundant features via step-wise VIF checks, and offer corporate interpretability.
  * **Decision Tree Classifier (`sklearn`)**: Built to capture complex non-linear interactions, subsequently optimized using pre-pruning constraints (`max_depth`, `min_samples_leaf`) to stop overfit training noise.

---

##  Primary Evaluation Optimization: Recall Focus
For this hospitality business case, **Recall was mathematically selected as the primary success metric** over standard Accuracy or Precision. 
* *Business Rationale*: A False Negative (missing an actual cancellation alert) is substantially more damaging to the hotel's bottom line than a False Positive (generating a false risk warning). Capturing every hidden cancellation allows management to execute protective overbooking or dynamic discounting models before the inventory value expires.
* **Threshold Optimization**: Moved the classification barrier away from the generic `0.5` level using ROC curve optimization to explicitly maximize Recall safety bounds.

---

##  Core Analysis & Key Business Insights
* **The Lead-Time Threat**: Lengthy booking lead times represent the highest correlation marker for eventual cancellation. Reservations booked far in advance exhibit extreme volatility.
* **Customer Loyalty Stabilization**: Repeat guests (`repeated_guest`) show remarkably flat, reliable reservation behavior, representing a high-retention, low-risk cluster.
* **Intent Signaling via Customization**: High volumes of `no_of_special_requests` act as a powerful proxy for customer commitment; guests heavily customized into specific room setups rarely cancel.
* **Dynamic Pricing Vulnerability**: Market segments featuring highly fluctuating `avg_price_per_room` metrics display increased cancellations, signaling strong price-sensitivity shifts.

---

##  Actionable Strategic Recommendations
* **Automated Risk Flagging System**: Deploy the final optimized model as an API to systematically score every inbound check-in, segmenting upcoming arrivals into Low, Medium, and High cancellation risk tiers.
* **Targeted Early Retention Pipelines**: Automate validation loops (automated confirmation texts, re-verification emails, deposits) targeting long-lead reservations as they approach critical windows.
* **Segmented Cancellation & Deposit Rules**: Apply dynamic, non-refundable deposit matrices or stricter cancellation horizons exclusively onto high-risk market segments, while maintaining fluid policies for verified repeat guests.

---

##  Repository Structure
* **`Automobile_Analysis_Project/`** — Project 1: Consumer behavioral distribution analysis.
* **`Inferential_Statistics_Coded_Project/`** — Project 2: Industrial quality control hypothesis model.
* **`ShowTime_Predictive_Modeling_Project/`** — Project 3: OTT streaming first-day linear regression tool.
* **`Hotel_Cancellation_Prediction_Project/`** (This folder)
  * `README.md` — Strategic outline, classification pipeline, and optimized metrics.
  * `Hotel_Cancellation_Classifier.ipynb` — Complete notebook detailing EDA visualizations, VIF treatments, Decision Tree pruning, and ROC threshold shifts.
  * `Hotel_Reservations.csv` — Full demographic and operational transaction records dataset.
