📊 Churn Analysis Project
This project is focused on Customer Churn Analysis using a combination of:

SQL Server for data cleaning and preparation

Python (scikit-learn) for machine learning classification

Power BI for visual insights and dashboards

The goal is to identify factors influencing customer churn, predict future churn behavior, and present actionable insights for business decisions.

✅ Overview

📦 Tech Stack

📂 Project Structure

📊 Power BI Insights

🧠 Machine Learning Overview

⚙️ Setup Instructions

🙌 Contribution Guidelines

🛠️ Tech Stack
Layer	Technology Used
Database	SQL Server (T-SQL)
Data Analysis	Python (pandas, numpy, scikit-learn)
Visualization	Power BI
Model Used	Random Forest Classifier


📁 Project Structure

📂 churn-analysis
│
├── sql/

│   └── churn_queries.sql               # Cleaned SQL scripts
│

├── images/

│   └── PowerBI_Churn_Insights.pdf      # Screenshot of Power BI insights

│

└── README.md
🧮 SQL Data Analysis & Cleaning
🔍 Data Exploration

-- Gender distribution
SELECT Gender, COUNT(*) AS TotalCount,
       COUNT(*) * 1.0 / (SELECT COUNT(*) FROM stg_Churn) AS Percentage
FROM stg_Churn
GROUP BY Gender;

-- Contract types
SELECT Contract, COUNT(*) AS TotalCount,
       COUNT(*) * 1.0 / (SELECT COUNT(*) FROM stg_Churn) AS Percentage
FROM stg_Churn
GROUP BY Contract;

-- Revenue contribution by Customer_Status
SELECT Customer_Status, COUNT(*) AS TotalCount,
       SUM(Total_Revenue) AS TotalRev,
       SUM(Total_Revenue) * 100.0 / (SELECT SUM(Total_Revenue) FROM stg_Churn) AS RevPercentage
FROM stg_Churn
GROUP BY Customer_Status;


🧹 Null Handling and Data Preparation
sql
Copy
Edit
-- Remove NULLs with default values
SELECT 
    ..., 
    ISNULL(Value_Deal, 'None') AS Value_Deal,
    ISNULL(Churn_Category, 'Others') AS Churn_Category,
    ISNULL(Churn_Reason, 'Others') AS Churn_Reason
INTO [dbo].[prod_Churn]
FROM [dbo].[stg_Churn];
👁️ Power BI Views

-- For Churn Analysis
CREATE VIEW vw_ChurnData AS
SELECT * FROM prod_Churn WHERE Customer_Status IN ('Churned', 'Stayed');

-- For Join Behavior Analysis
CREATE VIEW vw_JoinData AS
SELECT * FROM prod_Churn WHERE Customer_Status = 'Joined';
🤖 Python-Based Churn Prediction
Used Label Encoding for categorical variables and trained a RandomForestClassifier:

from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
model = RandomForestClassifier()
model.fit(X_train, y_train)
Model performance evaluated with confusion matrix and classification report.

📈 Power BI Dashboard
The Power BI dashboard provides visual insights on:

Churn distribution by Contract, State, and Gender

Revenue contribution by customer status

Predictive segments for high-risk churn customers

📥  Power BI Insights

---

## 📊 Power BI Dashboard Insights

Key findings from the Power BI dashboard visualizing churn behavior:

### ✅ Summary:
- **Total Customers**: 6,418  
- **Total Churned**: 1,732  
- **Churn Rate**: **27.0%**
- **New Joiners**: 411

---

### 🎯 Demographic Breakdown:
- **Churn by Gender**:  
  - **Male**: 64.15% of churned customers
- **Churn by Age**:  
  - Highest churn in **>70 years** (44.3%)
  - Followed by **31–40 age group** (23.1%)

---

### 🗺️ State-wise Churn:
- Highest in **Jammu & Kashmir (57.2%)**
- **Assam** and **Himachal Pradesh** also show higher churn

---

### 🧠 Customer Behavior Insights:
- **High churn in Month-to-Month contracts** (46.5%)
- **Fiber Optic internet users churn more** (57.9%)
- **Users not using Online Security churn more** (84.6%)

---

### 💳 Payment & Service Factors:
- **Customers paying via Mailed Check** show 87.8% churn  
- Services like **Device Protection**, **Online Backup**, and **Streaming TV** help **reduce churn**

---


## 🧮 SQL Workflow Summary

- **Data Exploration**:  
  - Analyzed distributions: `Gender`, `State`, `Contract`, `Customer_Status`
  - Detected nulls with aggregate `CASE WHEN` queries

- **Data Cleaning**:  
  - Used `ISNULL()` to replace nulls in service columns with meaningful defaults  
  - Loaded clean data into `prod_Churn`

- **Views for BI**:
  ```sql
  CREATE VIEW vw_ChurnData AS
  SELECT * FROM prod_Churn WHERE Customer_Status IN ('Churned', 'Stayed');

  CREATE VIEW vw_JoinData AS
  SELECT * FROM prod_Churn WHERE Customer_Status = 'Joined';


  # 🔍 Churn Analysis Project

A full-stack data analytics and machine learning project to identify and understand customer churn patterns using SQL, Power BI, and Python (Random Forest Classifier). This project enables actionable insights and supports strategic retention planning.

---

## 📦 Tech Stack

| Tool/Tech         | Purpose                         |
|------------------|----------------------------------|
| MySQL / SQL Server | Data Cleaning & Exploration     |
| Power BI         | Data Visualization               |
| Git/GitHub        | Version Control & Sharing        |

---

## 📂 Project Structure



📸 Sample Preview:

🚀 Getting Started
1. Setup Virtual Environment (Python)

python -m venv churn_env
source churn_env/bin/activate  # Windows: churn_env\Scripts\activate
pip install pandas numpy scikit-learn joblib

2. Connect SQL Server to Power BI
Load data using the view: vw_ChurnData

Build visuals using slicers, bar charts, and KPI cards

3. Run Python ML Notebook
Open notebooks/churn_model.ipynb to preprocess, train, and evaluate the model.



✅ Outcomes
Identified churn-prone demographics

Automated churn classification model

Built interactive dashboard for decision-makers

📬 Contact
gulshankumar02985@gmail.com

8709596674

https://www.linkedin.com/in/gulshankumar01/

For queries or collaboration, feel free to connect!
