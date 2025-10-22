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
- Using A/B tesing with Permutation ANOVA to find p-value:
- We can set some purpose for analysis:
  - Average wage, potential, overall of each value is different from each position (striker, deffender, midfelder)
  - Position which players play at is affected your international reputation.
  - To do hypothesis testing, first you can visualize to have a general picture
  
### Machine Learning Models
- **Logistic Regression**: Classification tasks.Ex: reputation, position
- **Linear Regression**: Predicting numerical values. Ex: potential, overall
- Performed statistical evaluations to assess the reliability of the regression model, including:
  - Checking the linearity of each feature
  - Constructing confidence intervals for each coefficient
  - Detecting outliers
  - Testing for multicollinearity


## Results & Insights
- Key findings from statistical tests
- Performance metrics of machine learning models
- Visualizations supporting insights

## Conclusion
This project provides an in-depth analysis of FIFA data using statistical and machine learning techniques in R. The insights gained offer a deeper understanding of player performance and attributes.
## Conclusion
This project provides an in-depth analysis of FIFA data using statistical and machine learning techniques in R.  
The insights gained offer a deeper understanding of player performance and attributes.

📄 **View full report:** [REPORT.pdf](https://github.com/khoathai710/EDA-fifa-data/blob/master/REPORT.pdf)
