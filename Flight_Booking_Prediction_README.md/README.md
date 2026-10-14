# Flight Booking Prediction

Predicting which customers of an aviation company are most likely to purchase a flight ticket, based on their digital and social media behavior, so that paid advertising can be targeted at high-propensity customers instead of the entire customer base.

## Business Problem

The company currently uses broad marketing (tele-calling and social media advertising) that is costly and converts only a small fraction of customers. This project builds predictive models to identify likely buyers, reducing wasted ad spend and improving conversion efficiency.

**Key requirement:** since device usage influences purchase behavior, **two separate models** were built, one for **Laptop** users and one for **Mobile** users (phones/tablets).

## Dataset

- **Size:** 11,760 customer records, 17 features (10,570 after duplicate removal)
- **Target:** `Taken_product` (Yes/No, whether the customer purchased a ticket)
- **Class balance:** ~84% No / ~16% Yes (imbalanced)
- **Feature groups:** social media engagement (page views, likes, comments), travel behavior (check-ins, network rating), demographics, preferred device and location type

## Project Workflow

1. **Business Understanding:** problem definition and the two-segment requirement
2. **Exploratory Data Analysis:** univariate, bivariate and multivariate analysis
3. **Data Preprocessing:** cleaning, duplicate removal, missing value imputation, outlier capping, feature engineering, SMOTE, scaling
4. **Baseline Model:** Logistic Regression
5. **Advanced Models:** Decision Tree, Bagging, Random Forest, AdaBoost, Gradient Boosting, XGBoost
6. **Hyperparameter Tuning:** `RandomizedSearchCV` on Random Forest, Gradient Boosting and XGBoost
7. **Model Comparison and Final Selection**
8. **Actionable Insights and Recommendations**

## Key Preprocessing Decisions

- Fixed data-entry errors (e.g., `"Three"` → 3, stray `"*"`, mixed `Yes/No` and `1/0` values)
- Consolidated 9 inconsistent `preferred_device` labels into two segments: **Laptop (1,108 rows)** and **Mobile (9,462 rows)**
- Median imputation for numeric columns (distributions were right-skewed), mode for categorical
- IQR-based outlier capping (rows kept, extreme values limited)
- **Duplicate removal after dropping `UserID`:** the ID column had been hiding **1,190 duplicate customers**, which inflated tree-based model scores until removed
- SMOTE and StandardScaler fit on **training data only**, after the train/test split, to prevent data leakage

## Results

**Metric of choice: F1-score**, because accuracy is misleading on an ~84/16 imbalanced target.

| Segment | Baseline (Logistic Regression) F1 | Final Model | Final F1 | Final ROC-AUC |
| Laptop | 0.586 | XGBoost (tuned) | **0.991** | 1.000 |
| Mobile | 0.436 | XGBoost (untuned) | **0.961** | 0.995 |

### Notable findings

- **Random Forest scored a perfect 1.000 F1 on Laptop.** This was diagnosed as overfitting on a small training set (886 rows), not real skill, and it was excluded from final selection.
- **Tuning did not always help.** It fixed overfitting and improved Gradient Boosting, but slightly reduced XGBoost's Mobile score (0.961 → 0.930). The final Mobile model is therefore the untuned XGBoost.

## Key Insights

- `following_company_page` is a top-2 predictor in both segments (followers convert at 30.5% vs. 10.4% for non-followers)
- **Laptop users:** destination preference (`Hill Stations`) is the strongest driver
- **Mobile users:** `Adult_flag` (life-stage) is the strongest driver
- Laptop users convert at 24.9% vs. 15.2% for Mobile users, which supports building separate models

## Business Recommendations

- Prioritize company-page followers in ad targeting across both segments
- Lead Laptop campaigns with destination-focused content
- Differentiate Mobile messaging by age/life-stage
- Use a higher confidence threshold before spending ad budget on Mobile predictions
- Validate with a pilot A/B test before full rollout

## Limitations

- The Laptop test set is small (222 rows), so its metrics can be noisy
- Very high scores should be validated on fresh, out-of-sample data before production use
- Hyperparameter search used a limited number of random iterations (`n_iter=20`)

## 🛠️ Tools & Technologies

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `Scikit-learn` · `Imbalanced-learn (SMOTE)` · `XGBoost` · `Google Colab`
