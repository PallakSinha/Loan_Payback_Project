# Predicting Loan Payback (Credit Risk Analysis)      

### Overview      
This project analyzes loan repayment behavior to identify factors influencing default risk and builds a machine learning model to predict whether a borrower will repay a loan.      
The focus is not only on model accuracy but also on business-relevant evaluation, particularly minimizing risky loan approvals.      

### Objective      
Predict whether a loan will be paid back (1) or defaulted (0)      
Identify key factors driving loan repayment      
Optimize model decisions using threshold tuning for real-world credit risk scenarios      

### Dataset      
The dataset contains borrower and loan-related features such as:      
- Annual Income      
- Debt-to-Income Ratio      
- Credit Score      
- Loan Amount      
- Interest Rate      
- Employment Status      
- Education Level      
- Loan Purpose      
- Grade/Subgrade (credit risk category)      

### Exploratory Data Analysis (EDA)      
Key insights:      
📉 Higher debt-to-income ratio → higher default risk      
📈 Higher credit score → higher repayment probability      
💼 Employment status strongly influences repayment      
💰 Higher interest rates are associated with defaults      
⚙️ Data Preprocessing      
Removed irrelevant features (id)      
Handled categorical variables using:      
  - Ordinal Encoding → grade_subgrade      
  - One-Hot Encoding → nominal features      
Implemented using ColumnTransformer + Pipeline

### Model      
Random Forest Classifier      
Handles non-linear relationships      
Robust to skewed data      
Suitable for tabular datasets   

#### Model Evaluation      
Metrics used:      
Confusion Matrix      
Classification Report      
ROC-AUC Score      

Key Insight:      
Accuracy alone is misleading due to class imbalance.      
Focus is placed on recall for defaulters (class 0).       

#### Threshold Optimization      
Instead of using default threshold (0.5), different thresholds were tested:      
Threshold	Default Recall	Accuracy      
0.3	0.63	0.90      
0.4	0.71	0.89      
0.5	0.77	0.87      
0.6	0.82	0.83      
0.7	0.90	0.73      
Final Choice: Threshold = 0.6      

- Captures 82% of defaulters      
- Reduces risky approvals      
- Maintains acceptable accuracy      

Confusion Matrix (Threshold = 0.6)      
Correctly identified ~20,000 defaulters      
Missed ~4,200 defaulters      
Flagged ~16,000 safe borrowers as risky      

Trade-off is acceptable in credit risk context.      
      
Feature Importance      

Top predictors:      

Employment Status      
Debt-to-Income Ratio      
Credit Score      
Grade/Subgrade      
Interest Rate      

### Business Insight      
Missing a defaulter is costlier than rejecting a safe borrower      
Threshold tuning improves risk control      
Model aligns with real-world lending strategies  

### Limitations      
Strong dependence on employment status      
Dataset may contain bias      

### Conclusion      
This project demonstrates a complete machine learning workflow with a strong emphasis on practical decision-making. By incorporating threshold tuning, the model becomes more aligned with real-world financial risk management.
