# Freddie-Mac-Capstone-Project__California
# Next Month Loan Performance Prediction & Analysis

## Project Overview
This project, conducted in collaboration with Freddie Mac, focuses on predicting loan transitions within 60 days in California using data spanning from 1999 to 2024. By analyzing historical trends across various economic conditions (e.g., the Great Recession, COVID-19 pandemic), the project aims to identify patterns in loan performance and enhance Freddie Mac's financial decision-making capabilities.

## Key Objectives
1. **Accurate Loan Transition Prediction**: Develop a model to forecast the monthly transitions of loans overdue by 60 days in California.
2. **Comprehensive Feature Analysis**: Identify and evaluate critical features such as loan-to-value ratios, borrower profiles, and economic indicators.
3. **Model Optimization and Validation**: Build, test, and refine the multinomial logistic regression model to ensure its accuracy and usability.
4. **Stakeholder Value**: Provide actionable insights for early risk management, data-driven strategies, and improved loan performance predictions.

## Data Highlights
### Data Sources
- **Primary Dataset**: Single Family Loan-Level Dataset ([Freddie Mac](https://www.freddiemac.com/research/datasets/sf-loanlevel-dataset))
  - Standard Origination Data (1999–2024): 40+ million rows
  - Standard Monthly Performance Data (1999–2024): 2000+ million rows
- **Supplemental Data**:
  - [Freddie Mac House Price Index (FMHPI)](https://www.freddiemac.com/research/indices/house-price-index): 260k rows
  - [California Unemployment Rate Data](https://data.ca.gov/dataset/civilian-unemployment-rate-for-us-and-california)

### Key Data Preparation Steps
- **Data Cleaning**:
  - Handled missing values using median/mode or related variables.
  - Standardized feature definitions across years.
- **Feature Selection**:
  - Focused on records where delinquency status equals 2 (over 60 days past due).
  - Generated approximately 480k records by including corresponding next-month records.
- **Feature Engineering**:
  - Created features like `LTV_Difference`, `Loan_Age_Percentage`, and dynamic unemployment rate changes.

## Model Description
- **Objective**: Predict the loan status for the next month (of 60 days past due).
- **Final Model**: Multinomial Logistic Regression
  - Chosen for its multi-class prediction capability, interpretability, and suitability for the problem.
  - Alternatives like Random Forest and XGBoost were considered but not selected due to their complexity, higher risk of overfitting, and lack of interpretability.
- **Training Process**:
  - Split data into training (pre-Jan 2019) and testing sets (post-Jan 2019).
  - Standardized features using `StandardScaler`.
  - Used `lbfgs` solver for optimization.

## Findings & Insights
1. **Model Performance**:
   - General Accuracy: 62%.
   - Strongest performance in predicting transitions to status 2 (60–89 days past due) and status 3 (90–119 days past due).
2. **Key Observations**:
   - Model underperformed during the COVID-19 pandemic (April 2020–July 2020) due to sudden surges in unemployment rates.
   - Borrowers with "Very Good" and "Exceptional" credit scores were observed to transition to worse statuses during the pandemic.

## Challenges & Workarounds
| Challenge                           | Workaround                                     |
|------------------------------------|-----------------------------------------------|
| Handling missing values            | Used median/mode and domain knowledge.        |
| Inconsistent data across years     | Standardized definitions across datasets.     |
| Model complexity and interpretability | Chose multinomial logistic regression for clarity. |

## Recommendations & Opportunities
1. Refine the model to incorporate insights from extraordinary economic events like the pandemic.
2. Conduct scenario analyses and stress tests to anticipate shifts in borrower behavior.
3. Develop early-warning systems and offer financial relief options to borrowers at risk of default.
4. Provide stability assurance mortgage products and financial counseling to borrowers.
