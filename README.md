# Exploratory Data Analysis on FIFA Data

## 1. Introduction
This project explores FIFA player data using statistical techniques (A/B Testing, ANOVA) and machine learning models in R.
<img width="864" height="486" alt="image" src="https://github.com/user-attachments/assets/58350b14-ab1c-48e8-8419-d62694a1686c" />

## 2. Tools & Libraries
The following R libraries are used for analysis:
- **tidyverse**: Data manipulation and visualization
- **ggplot2**: Data visualization
- **dplyr**: Data wrangling

## 3. Methodology

### 3.1 Data Cleaning & Preprocessing
- Handling missing values: In this case, missing values were kept as is, since they will later be handled using SMOTE during the model building phase.
- Transforming categorical variables
- Formatting numeric data: Cleaned and standardized numerical columns such as weight, height, and price by removing units (kg, $).


### 3.2 Exploratory Data Analysis (EDA)
- Conducted distribution checks of the dataset — this step is crucial as it can affect the accuracy of statistical methods such as ANOVA and help identify potential outliers.
<p align="center"> <img src="https://github.com/user-attachments/assets/5bf22726-dfe2-4ba6-9a93-dbeafbcaafdd" width="30%" /> <img src="https://github.com/user-attachments/assets/546ef878-6ee2-49be-8267-99e84d292887" width="30%" /> <img src="https://github.com/user-attachments/assets/218671eb-dd67-4636-b641-dd482b3eb46f" width="30%" /> </p>
- Performed statistical analyses to evaluate players’ potential and market value based on their positions and age groups.
<p align="center">
   <img width="30%" alt="image" src="https://github.com/user-attachments/assets/a6fa945d-ea29-4460-b019-f55a53208167" />

  <img width="30%" alt="image" src="https://github.com/user-attachments/assets/d9c1adc7-ebef-4c7f-bf34-34075bc86378" />

  <img width="30%" alt="image" src="https://github.com/user-attachments/assets/6889d387-d18b-4f04-a21c-d009ed5a12c5" />

</p>
- Find potential players are not playing for famous football team -> help coach find a potential player with affordable price.
<img width="606" height="270" alt="image" src="https://github.com/user-attachments/assets/8c3fc5b6-aad7-4bd5-9a32-67ffd5d37da8" />

### 3.3 A/B Testing

- Using A/B testing with Permutation ANOVA to find p-value.
- We can set some purposes for analysis:
  - Average wage, potential, and overall of each value are different among positions (striker, defender, midfielder).
  - The position where players play may affect their international reputation.
- To do hypothesis testing, first we can visualize to have a general overview.
  
  <img width="782" height="518" alt="image" src="https://github.com/user-attachments/assets/f23e179d-82dd-4b4e-b07f-351117b8158b" />

- From the visualization, Potential and Overall seem similar to the previous hypothesis, but to confirm this we use p-value with a maximum threshold of 0.05.
  - **H0:** Average wage, overall, potential, and value are the same across all positions.
  - **H1:** Average wage, overall, potential, and value are different across positions.

  <img width="712" height="297" alt="image" src="https://github.com/user-attachments/assets/30ee35d8-9d2b-4b21-b181-eb43d28815d3" />

- All p-values are less than 0.05, so we reject the null hypothesis (H0).
- **Conclusion:** Average wage, overall, potential, and value are different across positions.
- We apply the same method to the remaining variables.

### Machine Learning Models
- **Linear Regression:** Predicting numerical values.  
  Example: potential, overall.

- First, we explain some metrics:

  - **R² (Coefficient of Determination):**  
    Shows how well the model fits the data.  
    Ranges from 0 to 1 — closer to 1 means a better fit.

    **Formula:**  
    ```
    R² = 1 - (Σ(y_i - ŷ_i)² / Σ(y_i - ȳ)²)
    ```

  - **RMSE (Root Mean Square Error):**  
    Measures the average magnitude of prediction errors.  
    A lower RMSE means better model performance.

    **Formula:**  
    ```
    RMSE = sqrt( (1/n) * Σ(y_i - ŷ_i)² )
    ```

  - **MAE (Mean Absolute Error):**  
    Measures the average absolute difference between predicted and actual values.  
    Like RMSE, a lower MAE indicates better performance.

    **Formula:**  
    ```
    MAE = (1/n) * Σ|y_i - ŷ_i|
    ```

- We will perform the following steps:

  - **Step 1:** Use all features to build a baseline model and apply cross-validation to evaluate **R²**, **MAE**, and **RMSE**.  
    <img width="361" height="122" alt="image" src="https://github.com/user-attachments/assets/d04a8f78-ae4b-4e49-bcad-9cad10e87a01" />

  - **Step 2:** Use **Stepwise** or **Lasso Regression** — a technique where you add **λ (lambda)** to the loss function:  
    **Formula:**  
    ```
    L = (1/n) * Σ(y_i - ŷ_i)² + λ * Σ|w_j|
    ```
    - Stepwise regression helps determine the optimal number of features.  
      <img width="905" height="639" alt="image" src="https://github.com/user-attachments/assets/9c48dddb-625a-4c67-bd41-02a79d6b33c1" />
    - In Lasso, parameters are penalized — coefficients close to zero can be removed to simplify the model.

  - **Step 3:** Perform statistical evaluations to assess the reliability of the regression model, including:
    - Checking the **linearity** of each feature:  
      <img width="904" height="639" alt="image" src="https://github.com/user-attachments/assets/c3cc2d22-519a-4dc6-99bf-aff2c50abb00" />

    - Constructing **confidence intervals** for each coefficient:  
      <img width="904" height="638" alt="image" src="https://github.com/user-attachments/assets/f1fccc55-448b-4818-8b73-3f58a8c5531a" />  
      <img width="901" height="632" alt="image" src="https://github.com/user-attachments/assets/ab35f361-afb6-406f-bc9c-4f062a5adacb" />

    - Detecting **outliers:**  
      <img width="895" height="621" alt="image" src="https://github.com/user-attachments/assets/11968018-4ca6-427c-9a82-1831cfcc799d" />

    - Testing for **multicollinearity:**  
      <img width="548" height="593" alt="image" src="https://github.com/user-attachments/assets/75ec4d78-c561-4bfe-9aca-d3a8160dd7a2" />

  - **Step 4:** Enhance your model by using polynomial terms for some features.  
    ```r
    upgrade_model <- lm(formula = overall ~ poly(age, 4) + poly(value, 2) + poly(potential, 2) + ., data = data_train_lasso)
    result_display(upgrade_model, data_test, 'overall')
    ```

## Conclusion
This project provides an in-depth analysis of FIFA data using statistical and machine learning techniques in R.  
The insights gained offer a deeper understanding of player performance and attributes.

📄 **View full report:** [REPORT.pdf](https://github.com/khoathai710/EDA-fifa-data/blob/master/REPORT.pdf)
