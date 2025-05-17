## 🧠 Credit Risk Modeling with XGBoost – LendingClub Loan Data (2015–2016)

This project presents a complete end-to-end solution for predicting **loan default risk** using real-world LendingClub data. The primary goal is to build a robust, cost-aware machine learning model that can assist financial institutions in making smarter loan approval decisions and minimizing credit losses.

---

### 🔍 Objective

* Predict whether a loan applicant is **high-risk** or **low-risk** based on borrower and loan attributes.
* Optimize model performance using **repeated cross-validation** and **Gini coefficient** as the evaluation metric.
* Incorporate **business cost-benefit assumptions** to select the optimal decision threshold for loan approvals.

---

### 📊 Dataset

* **Source**: LendingClub loan applications for the years 2015 (training) and 2016 (OOT testing).
* **Target Variable**: `Outcome` → 1 for **high-risk** (Charged-Off or Late), 0 for **low-risk** (Fully Paid or Current).

---

### 🧱 Key Components

#### ✅ Data Preparation & Feature Engineering

* Converted raw fields (e.g., `term`, `emp_length`, `sub_grade`) into numeric formats.
* Engineered meaningful features such as:

  * `loan_to_income`, `payment_to_income`, `combined_risk_score`, `int_rate_term_interaction`, etc.
* Created bucketed variables and interaction terms to capture borrower behavior.

#### ✅ Exploratory Data Analysis

* Investigated feature distributions, correlations, risk segmentations, and temporal shifts between years.

#### ✅ Model Development

* Algorithm: `XGBoost` (tree-based gradient boosting).
* Evaluation: **Gini coefficient** and **ROC AUC**.
* Validation: **Repeated 5-fold cross-validation** using 3 different seeds (total 15 evaluations).
* Performance:

  * **Train Gini**: 0.5237
  * **OOT Gini**: 0.4002 (2016 data)

#### ✅ Cost-Aware Threshold Optimization

* Incorporated realistic **business costs**:

  * True Negative (approved good loan): **+\$300**
  * False Negative (approved bad loan): **–\$1000**
* Identified the **optimal score threshold** that maximizes expected profit.

#### ✅ Model Explainability

* Used **Partial Dependence Plots (PDP)** and **ICE curves** to understand how top features affect predictions.
* Identified intuitive, actionable drivers of loan risk.

---

### 📦 Deliverables

* 📝 `Jupyter Notebook` – Full workflow with code, explanations, and visualizations.
* 📈 PDP & threshold optimization visualizations.
* 📂 Reusable functions and pipeline objects.
* 🎯 Business-ready model selection and deployment logic.

---

### 📌 Business Impact

This model supports:

* **Automated underwriting**: Flagging high-risk applicants before approval.
* **Risk-based pricing**: Adjusting rates based on predicted default probabilities.
* **Portfolio monitoring**: Identifying segments with shifting risk profiles.

---

### 🚀 Future Enhancements

* Add **SHAP explanations** for local feature importance.
* Integrate **external credit score APIs** (e.g., FICO).
* Deploy as a **Flask or FastAPI model scoring service**.

---
