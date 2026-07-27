# Insurance Charges Prediction Project

## 1. Introduction
This project aims to analyze and predict individual medical insurance charges using various personal attributes such as age, sex, BMI, number of children, smoking status, and region. The goal is to understand the factors influencing insurance costs and build a robust prediction model.

## 2. Dataset
The dataset used for this analysis is `insurance (1).csv`,Heart.CSV  which contains 1338 entries and 7 features:
- `age`: Age of the primary beneficiary (integer)
- `sex`: Gender of the primary beneficiary (male/female)
- `bmi`: Body mass index (BMI) (float)
- `children`: Number of children covered by health insurance (integer)
- `smoker`: Smoking status (yes/no)
- `region`: Residential area in the US (northeast, northwest, southeast, southwest)
- `charges`: Individual medical costs billed by health insurance (float)

## 3. Data Preprocessing
The following steps were performed to clean and prepare the data:
- **Duplicate Handling**: One duplicate entry was identified and removed.
- **Categorical Feature Encoding**:
    - `sex` was mapped to `is_female` (0 for male, 1 for female).
    - `smoker` was mapped to `is_smoker` (0 for no, 1 for yes).
    - `region` was one-hot encoded, creating binary columns for each region (`region_northwest`, `region_southeast`, `region_southwest`), dropping the first to avoid multicollinearity.
- **Feature Engineering (BMI Category)**:
    - A new categorical feature `bmi_category` was created from `bmi` (underweight, healthy, overweight, obese).
    - `bmi_category` was then one-hot encoded into `bmi_category_healthy`, `bmi_category_overweight`, and `bmi_category_obese`, dropping the first category.
- **Data Type Conversion**: All boolean (True/False) columns resulting from one-hot encoding were converted to integer (0/1).
- **Feature Scaling**: Numerical features (`age`, `bmi`, `children`) were standardized using `StandardScaler` to have a mean of 0 and a standard deviation of 1.

## 4. Exploratory Data Analysis (EDA)
Initial EDA involved:
- **Shape and Information**: Checked the dimensions and data types of the dataset.
- **Descriptive Statistics**: Summarized numerical features.
- **Missing Values**: Confirmed no missing values in the dataset.
- **Visualizations**:
    - Histograms for numerical columns (`age`, `bmi`, `children`, `charges`) to observe their distributions.
    - Count plots for categorical columns (`children`, `sex`, `smoker`) to see their frequencies.
    - Box plots for numerical columns to identify outliers.
    - A heatmap showing correlations between numerical features.

## 5. Feature Analysis

### 5.1. Pearson Correlation Analysis
Pearson correlation was calculated between several features and `charges` to identify linear relationships. Key findings include:
- `charges` is perfectly correlated with itself (1.0).
- `is_smoker` has a strong positive correlation with `charges` (0.79).
- `age` and `bmi` also show positive correlations (0.30 and 0.20 respectively).
- `bmi_category_obese` shows a positive correlation (0.20).
- `is_female`, `bmi_category_healthy`, and `bmi_category_overweight` show slight negative correlations.

### 5.2. Chi-squared Test for Categorical Associations
A Chi-squared test was performed to examine the association between various categorical features and `is_smoker`.
- `is_female` and `region_southeast` show a statistically significant association with `is_smoker` (p-values < 0.05).
- `region_northwest`, `region_southwest`, and the `bmi_category` features did not show a statistically significant association with `is_smoker`.

## 6. Next Steps
- **Model Building**: Implement various regression models (e.g., Linear Regression, Random Forest, Gradient Boosting) to predict insurance charges.
- **Model Evaluation**: Evaluate models using appropriate metrics (e.g., R-squared, MAE, RMSE).
- **Hyperparameter Tuning**: Optimize model performance using techniques like GridSearchCV or RandomizedSearchCV.
- **Feature Importance**: Analyze feature importance to understand which features contribute most to the prediction.

## 7. How to Run
1. Upload the `insurance (1).csv` file to your Colab environment.
2. Run all cells in the notebook sequentially.










# Heart Disease Prediction Notebook

This notebook performs an exploratory data analysis (EDA) and data preprocessing on a heart disease dataset. The steps include:

1.  **Data Loading**: Loading the `heart.csv` dataset.
2.  **Initial Data Exploration**: Examining columns, data types, descriptive statistics, and checking for duplicates and missing values.
3.  **Data Cleaning**: Handling zero values in 'Cholesterol' and 'RestingBP' by replacing them with the mean of non-zero values.
4.  **Visualizations**: Generating various plots to understand data distributions and relationships.
5.  **Feature Engineering**: Encoding categorical variables using one-hot encoding and scaling numerical features using `StandardScaler`.
