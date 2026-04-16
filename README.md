# 📊 MoMo Financial Analysis Dashboard

**Turning personal mobile money transactions into actionable financial insights**

---

## 📌 Overview

This project presents an end-to-end **Power BI analysis of personal Mobile Money (MoMo) transactions for 2025**, designed to uncover patterns in spending, saving, and investment behavior.

The dashboard goes beyond basic visualization by combining:
- Financial behavior analysis  
- Context-driven interpretation  
- Actionable recommendations  

👉 The goal is to understand **how money flows, how it is allocated, and how financial discipline evolves over time**.

---

## 🎯 Project Objectives

- Analyze transaction activity and trends  
- Identify spending patterns and key expense drivers  
- Evaluate savings consistency and growth  
- Track investment contributions and behavior  
- Assess overall financial health  

---

## 🧠 Business Questions

### 💳 Transactions
- What is the total transaction volume and value?
- When are transactions most active (AM vs PM)?
- How do transactions trend over time?

### 📶 Data Bundle
- How much is spent on data bundles?
- How frequently are bundles purchased?
- How did pricing changes affect spending?

### 💰 Savings (Yello Save)
- How consistent is saving behavior?
- What is the total amount saved?
- How did savings evolve over time?

### 📈 Investments
- How much is invested?
- What share of expenses goes into investments?
- How do investments grow month-over-month?

### 💸 Expenses
- What are the major spending categories?
- Who are the top recipients?
- Why are certain expenses higher?

### 🧾 Financial Health
- Is the net financial position improving?
- How is income distributed across spending, savings, and investments?
- Is a negative balance due to overspending or strategy?

---

## 📊 Dashboard Pages

### 1️⃣ Transaction Overview
![Transaction Page](images/Transaction%20Page.png)

- Transaction volume and value  
- AM vs PM activity patterns  
- Weekly and monthly trends  

---

### 2️⃣ Data Bundle Spending & Usage
![Data Bundle](images/Data%20bundle.png)

- Total spending and purchase frequency  
- Quarterly distribution  
- Pricing impact analysis  

📌 **Insight:**  
Spending increased after a pricing shift from **GHS 350 → GHS 399**, reflecting higher value bundles.

---

### 3️⃣ Yello Save Savings & Consistency
![Yello Save](images/Yello%20save.png)

- Total savings: **GHS 15,388+**  
- Consistency rate: **98% (359 days)**  

📌 **Insight:**  
Savings increased after mid-year adjustment from **GHS 32 → GHS 52**, supported by automation.

---

### 4️⃣ Investment Analysis
![Investment](images/Investment.png)

- Total investment value  
- Contribution trends  
- Monthly growth  

📌 **Insight:**  
Investment activity increased in later months, indicating a shift toward long-term financial planning.

---

### 5️⃣ Expense Analysis
![Expenses](images/Expenses.png)

- Spending categories  
- Top recipients  
- Monthly trends  

📌 **Context:**  
Higher healthcare spending reflects real-life medical conditions, not discretionary overspending.

---

### 6️⃣ Financial Health Summary
![Financial Health Summary](images/Financial%20Health%20Summary.png)

- Net financial position  
- Income vs expenses  
- Savings rate  
- Allocation trends  

📌 **Insight:**  
Low/negative balances reflect **active fund transfers and investments**, not poor financial management.

---

## 📈 Key Insights

- Strong savings discipline with **98% consistency**
- Increased savings after mid-year adjustment
- Growing investment contributions toward year-end
- High medical expenses driven by real-life conditions
- Financial behavior reflects **intentional cash management**

---

## 🧠 Insights & Interpretation

This analysis reflects a structured financial approach:

- Funds are actively moved across platforms (MoMo → Bank → Investments)
- Savings behavior is automated and consistent
- Spending patterns are largely necessity-driven
- Investment activity increases with financial stability

👉 Overall, the data shows **discipline, adaptability, and long-term financial focus**.

---

## 💡 Key Recommendations

### 1. Track Cross-Platform Finances
Integrate MoMo, bank, and investment data for a complete financial view.

---

### 2. Maintain Automated Savings
Automation proved highly effective—continue and scale contributions over time.

---

### 3. Strengthen Investment Strategy
Track performance and diversify investment allocations.

---

### 4. Plan for Healthcare Costs
Introduce a structured healthcare budget or financial buffer.

---

### 5. Improve Financial Visibility
Build a unified dashboard combining all financial accounts.

---

### 6. Introduce Budget Controls
Set spending benchmarks and monitor deviations monthly.

---

## 🧰 Tools & Technologies

- Power BI  
- DAX  
- Power Query  
- Excel  

---

## 🧮 DAX Measures

<details>
<summary>Click to view all DAX measures</summary>

```DAX
-- INCOME
Total Income =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[TRANS. TYPE] <> "DEBIT"
)

-- EXPENSES
Total Expenses =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[TRANS. TYPE] = "DEBIT"
)

Total Other Expenses =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[TRANS. TYPE] = "DEBIT",
    NOT 'MoMo_Transactions'[OVA] IN {
        "yelloAD.sp",
        "ICS3.sp",
        "HubtelPos",
        "zpcot.sp"
    }
)

-- TRANSACTIONS
Total Transactions =
COUNT('MoMo_Transactions'[F_ID])

Total Debit Transactions =
CALCULATE(
    COUNT('MoMo_Transactions'[F_ID]),
    'MoMo_Transactions'[TRANS. TYPE] = "DEBIT"
)

Total Credit Transaction Amount =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[TRANS. TYPE] <> "DEBIT"
)

-- DATA BUNDLE
Total Data Bundle Spending =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[AMOUNT] IN {350, 399},
    'MoMo_Transactions'[TRANS. TYPE] = "DEBIT"
)

-- SAVINGS
Total Yello Save Savings =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[AMOUNT] IN {32, 52},
    'MoMo_Transactions'[TRANS. TYPE] = "DEBIT"
)

-- INVESTMENT
Total Investment =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[OVA] IN {"ICS3.sp","HubtelPos","zpcot.sp"},
    'MoMo_Transactions'[TRANS. TYPE] = "DEBIT"
)

-- FINANCIAL HEALTH
Net Financial Position =
[Total Income] - [Total Expenses]
