## 📝 Project Description

This project focuses on developing and comparing predictive models to estimate the **Final Weight (lbs)** of subjects in a dietary study. The dataset includes demographic, lifestyle, physiological (BMR, caloric intake), and weight change variables.

### Key Findings and Model Performance

The analysis consistently highlighted the importance of metabolic and caloric factors for accurate prediction:

* **Impact of BMR:** The **Basal Metabolic Rate (BMR)** is confirmed as a significant predictor, as models including BMR consistently achieved **higher $R^2$ scores and lower RMSE** across all approaches. Excluding BMR reduces the models' predictive power, with the reduction being more **pronounced for women**.
* **BMR Proxy:** When BMR is unavailable, **Daily Calories Consumed (DCC)** acts as a strong proxy due to its high correlation (0.7) with BMR, allowing models to still perform well. However, predictions are generally **less precise** without BMR.
* **Optimal Global Model:** The best balance of accuracy and efficiency is achieved by a **global linear model using Mini-Batch Gradient Descent (MBGD)**, particularly when BMR is included. MBGD showed slightly better results with faster convergence and reduced noise compared to other global approaches.
* **Model Complexity:** The similarity in results across various methods (Linear Regression, Gradient Descent, Lasso, and Ridge) suggests that the relationship between features and the target variable is **best captured by a straightforward linear approach**.
* **Regularization:** Both **Lasso** and **Ridge Regression** confirmed that caloric metrics (Daily Caloric Surplus/Deficit and Daily Calories Consumed) become critical predictors when BMR is unavailable.
* **Gender Stratification:** While gender-stratified models provide deeper insights, a global model is generally preferable for predictive performance. **Men achieved a higher $R^2$ overall** in the stratified analysis, suggesting the included features were more predictive of final weight in males under these conditions.

### Data Preparation Highlights

The data was rigorously prepared through:

* **Imputation:** Missing **Gender** values were imputed using KNN and regression-based methods. Missing **Daily Caloric Surplus/Deficit** values were calculated directly from other features.
* **Outlier Handling:** Unrealistic **Age** values were removed, but relevant outliers in features like **Daily Calories Consumed** were retained to avoid biasing the model.
* **Feature Transformation:** Numerical features were **standardized** to optimize model convergence. Categorical features were encoded using **binary (0/1)** for gender/smoking, **ordinal encoding** for factors like Physical Activity Level, and **one-hot encoding** for nominal variables like Work Sector.

---

## 💾 README for the Predictive Weight Modeling Project

---

## ⚖️ Predictive Modeling for Final Weight in Dietary Study

This repository contains the analysis for the Supervised Learning Midterm Project, which focuses on developing robust predictive models to estimate the **Final Weight (lbs)** of participants in a dietary study. The analysis thoroughly explores the dataset, addresses data quality issues, and compares various linear and regularization models under different feature conditions.

---

### 🎯 Key Project Goals

1.  Predict the target variable: **Final Weight (lbs)**.
2.  Evaluate the predictive value of **Basal Metabolic Rate (BMR)**, comparing model performance with and without its inclusion.
3.  Compare linear and gradient descent approaches (Batch, Mini-Batch) and regularization models (Lasso, Ridge).
4.  Assess the value of **gender-stratified modeling** versus a single global model.

---

### 💡 Core Findings

| Area | Insight | Citation |
| :--- | :--- | :--- |
| **BMR Importance** | BMR is a **key predictor**; its inclusion consistently leads to **higher $R^2$ and lower RMSE**. The improvement is **more pronounced for women**.
| **BMR Alternative** | When BMR is absent, **Daily Calories Consumed (DCC)** becomes the critical feature, acting as a high-correlation (0.7) proxy for BMR.
| **Optimal Model** | The best approach is the **global linear model with Mini-Batch Gradient Descent (MBGD) and BMR included**, as it balances accuracy and computational efficiency
| **Model Complexity** | The relationship between features and final weight is fundamentally **linear**, making simple models most effective and ruling out the need for complex, non-linear methods
| **Gender Stratification** | **Men achieved a higher overall $R^2$** in stratified models, suggesting the current features are slightly more predictive for the male cohort. Gender-specific models are useful for deeper insights but may struggle without BMR.

---

### 🔧 Data Preparation and Modeling Steps

1.  **Data Quality:** Handled missing values through KNN/regression imputation for **Gender** and calculation for **Daily Caloric Surplus/Deficit**. Outliers in core features were mostly **retained** to prevent biasing the weight-change model].
2.  **Feature Engineering:** Numerical features were **standardized**; categorical features were mapped using **binary, ordinal, and one-hot encoding** where appropriate to preserve interpretability and structure.
3.  **Dimensionality Reduction:** **ANOVA, RFE, and Model-Based Selection** were applied to identify the most influential and non-redundant feature subset.
4.  **Modeling Comparison:**
    * **Linear Regression (Sklearn):** Established as the baseline
    * ]**Gradient Descent:** Mini-Batch Gradient Descent proved superior to Batch Gradient Descent, showing faster, stabler convergence with moderate batch sizes.
    * **Regularization (Lasso & Ridge):** Used with an augmented dataset to improve generalization and handle multicollinearity. Both confirmed the central role of caloric metrics.
