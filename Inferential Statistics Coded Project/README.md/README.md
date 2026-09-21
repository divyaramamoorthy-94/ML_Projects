# Decision Making with Business Statistics

A comprehensive statistical data analysis project focusing on applying probability theory, distribution modeling, hypothesis testing, and multi-factor Analysis of Variance (ANOVA) to resolve real-world operational and quality control challenges.

---

## Project Overview & Business Problems
This project applies rigorous statistical methodologies across four unique business verticals to drive data-driven decision-making, optimize production quality, and maintain process control:

1. **Sports Analytics (Probability)**: Investigating injury exposure patterns across different football playing positions to optimize training and player safety.
2. **Quality Control & Packaging (Normal Distribution)**: Modeling the breaking strength of cement packaging gunny bags to predict material durability and manage transportation risks.
3. **Manufacturing & Surface Material Specs (Hypothesis Testing)**: Statistically verifying if raw material hardness levels meet quality boundaries required for industrial stone printing at Zingaro Company.
4. **Healthcare Operational Excellence (ANOVA)**: Decoding how various independent factors—including specific dentists, implant preparation methods, and raw alloys—interact to impact dental implant structural hardness.

---

## Technical Methodology & Python Frameworks
The data engineering, computation, and statistical inferences were executed cleanly using industry-standard Python libraries:
* **`Pandas` & `NumPy`**: Used for structural data handling, filtering, conditional segmentation, and descriptive aggregation.
* **`SciPy.stats`**: Leveraged for computing precise Z-scores, Normal Cumulative Distribution Functions (CDF), and parametric T-tests.
* **`Statsmodels`**: Applied to configure multi-way Analysis of Variance (ANOVA) tables and calculate F-statistics to evaluate variable interactions.
* **`Matplotlib`**: Used to plot continuous probability density functions (PDF) to visualize distribution curves and highlight outlier rejection regions.

---

## Core Analysis & Key Statistical Insights

### 1. Probability Analysis (Player Injuries)
* **Overall Baseline**: Analysis showed a high total injury exposure rate, with **61.7%** of the tracked player base experiencing foot injuries.
* **Conditional Risks**: Strikers account for **31%** of all injured players, indicating statistically higher physical stress or collision risks unique to attacking configurations.

### 2. Normal Distribution Analysis (Packaging Durability)
* Based on an empirical distribution (\(\mu = 5\text{ kg/cm}^2\), \(\sigma = 1.5\)), **82.5%** of production runs safely satisfy a robust baseline strength criteria (\(\ge 3.6\text{ kg/cm}^2\)).
* Conversely, **11.1%** of bags fall below the critical threshold (\(< 3.17\text{ kg/cm}^2\)), exposing logistics to high material tearing risks, while **13.9%** fall completely outside the target operational interval (\(3\text{ to }7.5\text{ kg/cm}^2\)).

### 3. Hypothesis Testing (Zingaro Printing Quality)
* **One-Sample T-Test (\(t = -4.165\), \(p < 0.0001\))**: Rejected the null hypothesis with high confidence, proving that raw, unpolished stones fail to meet the required Brinell hardness threshold of 150.
* **Two-Sample T-Test (\(t = 3.242\), \(p = 0.0016\))**: Reverted clear statistical validation that mechanical surface polishing provides a statistically significant increase in structural hardness, making material fit for operational use.

### 4. ANOVA Analysis (Dental Implant Optimization)
* **Operator Effect**: The differences among individual dentists yielded \(p > 0.05\), confirming that the operator has no statistically significant impact on implant hardness. The system reflects a highly reliable, standardized procedure.
* **Method Effect**: Implant preparation methods yielded \(p < 0.05\), indicating that the preparation technique is the primary driver of product hardness. Specifically, **Method 3** produces significantly higher, premium hardness outputs compared to baseline methods.
* **Alloy Interactions**: For Alloy 1, a significant interaction effect was detected between the dentist and the method, meaning specific operators excel with specific techniques. For Alloy 2, no interaction was found, making outcomes universally consistent.

---

## Executive Recommendations
* **Process Standardization**: Transition product lines exclusively to **Method 3** for implant preparations to uniformly maximize structural hardness and longevity across all alloys.
* **Manufacturing Interventions**: Mandate a surface-polishing phase for printing stones to systematically mitigate material fracturing and ensure ink placement accuracy.
* **Supply Chain Capping**: Fine-tune the cement bag extrusion processes to squeeze down the variance (\(\sigma\)), pulling the 11.1% tail of weak bags into safe operational tolerances to minimize shipping wastage.

---

## Repository Structure
* **`Inferential Statistics Coded Project/`** (This folder)
  * `README.md` — Project abstract, technical framework, and executive summary.
  * `Statistical_Analysis_Notebook.ipynb` — Interactive Python file detailing equations, CDF distributions, T-tests, and ANOVA calculations.
  * `datasets/` — Raw text assets covering material matrices, injury logs, and treatment outputs.
