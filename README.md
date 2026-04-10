
# 📊 MoMo Financial Analysis Dashboard

**Turning personal mobile money transactions into actionable financial insights**

---

## 📌 Overview

This project presents a comprehensive **Power BI dashboard** analyzing personal Mobile Money (MoMo) transactions for the year **2025**.

The dashboard transforms raw transactional data into meaningful insights across:

- Transaction activity and trends  
- Spending patterns and expense behavior  
- Savings discipline (Yello Save)  
- Investment growth and contributions  
- Overall financial health  

The objective is to understand **how money flows, how it is allocated, and how financial discipline evolves over time**.

---

## 🧠 Business Questions

This analysis was guided by key questions:

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

---

### 1️⃣ Transaction Overview

- Total transactions and value  
- AM vs PM activity  
- Weekly transaction patterns  
- Monthly trends  

![Transaction Page](images/Transaction%20Page.png)

---

### 2️⃣ Data Bundle Spending & Usage Analysis

- Total data bundle spending  
- Purchase frequency  
- Quarterly distribution  
- Average bundle cost  

📌 **Insight:**  
Data bundle spending increased in the second half of the year due to a pricing change from **GHS 350 (90GB)** to **GHS 399 (214GB)**.

![Data Bundle](images/Data%20bundle.png)

---

### 3️⃣ Yello Save Savings & Consistency Analysis

- Total savings: **GHS 15,388+**  
- Savings consistency: **98% (359 days)**  
- Average daily savings  

📌 **Key Insight:**  
Savings increased significantly after **June 2025**, when daily savings changed from **GHS 32 → GHS 52**.

📌 **Behavior Insight:**  
Automated savings ensured strong financial discipline and consistency.

![Yello Save](images/Yello%20save.png)

---

### 4️⃣ Investment Growth & Contribution Analysis

- Total investment value  
- Investment share (%)  
- Monthly growth trend  
- Quarterly distribution  

📌 **Insight:**  
Investment contributions increased in later months, indicating a shift toward long-term financial planning.

![Investment](images/Investment.png)

---

### 5️⃣ Expense Analysis & Spending Patterns

- Spending by category  
- Top payees  
- Monthly expense trends  

📌 **Context:**  
Higher expenses on medication and healthcare were observed due to health challenges during the year.

👉 This explains increased spending in medical-related categories.

![Expenses](images/Expenses.png)

---

### 6️⃣ Financial Health Summary

- Net Financial Position  
- Total Income vs Expenses  
- Savings Rate  
- Monthly financial allocation  

📌 **Key Insight:**  
The negative net position reflects **active cash movement**, not overspending.

👉 Funds are frequently:
- Transferred to bank accounts  
- Invested  

📌 **Conclusion:**  
This indicates **intentional financial management and disciplined money allocation**.

![Financial Health Summary](images/Financial%20Health%20Summary.png)

---

## 📈 Key Insights

- Strong savings discipline with **98% consistency (359 days)**
- Increase in savings after mid-year adjustment (GHS 32 → GHS 52)
- Growing investment contributions toward year-end
- High medical expenses driven by real-life health conditions
- Financial behavior reflects **strategic cash management**, not overspending

---

## 🧰 Tools & Technologies

- **Power BI** – Dashboard design  
- **DAX** – Calculations and KPIs  
- **Power Query** – Data transformation  
- **Excel** – Data preparation  

---

## 🧮 DAX Measures (Click to Expand)

---

### 💰 Income

<details>
<summary>View DAX</summary>

```DAX
Total Income =
CALCULATE(
    SUM('MoMo_Transactions'[AMOUNT]),
    'MoMo_Transactions'[TRANS. TYPE] <> "DEBIT"
)
