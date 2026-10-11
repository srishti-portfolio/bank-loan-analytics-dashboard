# 🏦 Bank Loan Analytics Dashboard (Power BI)

A two-page interactive Power BI dashboard that analyses a bank's lending portfolio of **38,576 loan applications worth $435.8M** issued during 2021. It tracks portfolio health through five core KPIs, separates **good loans from bad loans**, and breaks lending activity down by month, state, term, home ownership and purpose, helping the bank monitor repayment behaviour and shape its lending strategy.

### 📍 Page 1 — Summary

<img width="1202" height="676" alt="Bank Loan Analytics Dashboard Summary" src="https://github.com/user-attachments/assets/dda9e03a-9c80-4dcc-92be-9e2e68177d02" />


### 📍 Page 2 — Overview

<img width="1205" height="678" alt="Bank Loan Analytics Dashboard Overview" src="https://github.com/user-attachments/assets/7d334252-f9bb-4379-9e6a-86861228b06e" />


---

## 📌 Problem Statement

The bank needs a comprehensive loan report to monitor and assess its lending activities and performance. The dashboard should:

- Provide insight into key loan metrics and how they change over time.
- Track the health of the loan portfolio by splitting **good loans** from **bad loans**.
- Monitor funded amounts, repayments, interest rates and borrower debt-to-income ratios.
- Visualise lending operations across time, geography, loan term, home ownership and purpose.
- Support data-driven decisions on lending strategy and risk.

---

## 📊 Key Performance Indicators (KPIs)

| KPI | Description | Value |
|---|---|---|
| **Total Loan Applications** | Number of applications received | **38,576** |
| **Total Funded Amount** | Total funds disbursed as loans | **$435.8M** |
| **Total Amount Received** | Total repayments collected from borrowers | **$473.1M** |
| **Average Interest Rate** | Average rate charged across all loans | **12.05%** |
| **Average DTI Ratio** | Average borrower debt-to-income ratio | **13.33%** |

### Good Loans vs Bad Loans

A loan is classed as **good** when its status is *Fully Paid* or *Current*, and **bad** when it is *Charged Off*.

| Category | Applications | Share | Funded Amount | Amount Received |
|---|---|---|---|---|
| ✅ **Good Loans** | 33,243 | **86.18%** | $370.2M | $435.8M |
| ❌ **Bad Loans** | 5,333 | **13.82%** | $65.5M | $37.3M |

---

## 📈 Dashboard Pages and Visuals

### Page 1 — Summary (portfolio health)

| Visual | Chart Type | Purpose |
|---|---|---|
| Good Loan Issued | Donut chart + cards | Share of good loans with their applications, funded amount and repayments |
| Bad Loan Issued | Donut chart + cards | Share of bad loans with their applications, funded amount and repayments |
| Funded Amount vs Repayment | Clustered column chart | Compares money lent against money recovered for each loan status |
| Loan Application | Column chart | Application count by loan status |
| Average Interest Rate | Column chart | Average interest rate by loan status |
| Average DTI Ratio | Column chart | Average borrower DTI by loan status |

### Page 2 — Overview (lending operations)

| Visual | Chart Type | Purpose |
|---|---|---|
| Monthly Loan Applications | Line chart | Month-by-month application trend across the year |
| Loan Applications by State | Filled map (Azure Maps) | Geographic spread of lending across 50 states |
| Loan Applications by Term | Donut chart | Split between 36-month and 60-month loans |
| Loan Applications by Home Ownership | Bar chart | Applications by Rent, Mortgage, Own, Other and None |
| Loan Applications by Purpose | Tree map | Breakdown of why borrowers took the loan |

### 🎛️ Filters and Navigation

- **Purpose slicer:** 14 categories, from debt consolidation to weddings
- **Grade slicer:** Risk grades A to G
- **Page navigation buttons:** Switch between Summary and Overview
- **Reset filter button:** Clears all slicers in one click

---

## 💡 Key Insights

- **Repayments exceed disbursements overall.** The bank received **$473.1M** against **$435.8M** funded, an inflow of about **$37.3M** from interest.
- **Bad loans are the main leak.** Charged-off loans recovered only **$37.3M of the $65.5M** lent, a shortfall of roughly **$28.2M** and a recovery rate near **57%**.
- **Risk shows in the rate and the DTI.** Charged-off borrowers carried a higher average interest rate (**13.88%** vs **11.64%** for fully paid) and a higher average DTI (**14.00%** vs **13.17%**), so both are useful early warning signals.
- **Lending grew steadily all year.** Monthly applications rose from **2,332 in January to 4,314 in December**, an increase of about **85%**.
- **Debt consolidation dominates.** It accounts for **18,214 applications (47%)**, far ahead of credit card loans (4,998).
- **Short-term loans are preferred.** **73%** of borrowers chose the 36-month term (28,237) over 60 months (10,339).
- **Renters and mortgage holders drive volume.** Together they make up **35,637 applications (92%)** of the portfolio.
- **Lending is geographically concentrated.** California (6,894), New York (3,701), Florida (2,773) and Texas (2,664) lead the 50 states.

---

## 🗂️ Dataset

A single table, `financial_loan`, with **38,576 rows and 23 columns** covering loans issued between **1 January and 12 December 2021**.

| Column | Description |
|---|---|
| `ID` / `MEMBER_ID` | Unique identifiers for the loan application and the customer |
| `ISSUE_DATE` | Date the loan was issued |
| `LOAN_AMOUNT` | Amount approved and funded |
| `TOTAL_PAYMENT` | Total amount repaid by the borrower |
| `INT_RATE` | Interest rate charged on the loan |
| `DTI` | Debt-to-income ratio of the borrower |
| `INSTALLMENT` | Fixed monthly payment |
| `TERM` | Repayment duration (36 or 60 months) |
| `LOAN_STATUS` | Fully Paid, Current or Charged Off |
| `GRADE` / `SUB_GRADE` | Risk grade assigned by the bank (A = lower risk, G = higher risk) |
| `PURPOSE` | Reason for the loan |
| `HOME_OWNERSHIP` | Rent, Mortgage, Own, Other or None |
| `ADDRESS_STATE` | Borrower's state |
| `ANNUAL_INCOME` | Yearly income of the borrower |
| `EMP_LENGTH` / `EMP_TITLE` | Years employed and job title |
| `VERIFICATION_STATUS` | Whether the bank verified the borrower's income |
| `TOTAL_ACC` | Number of credit accounts held |
| `LAST_PAYMENT_DATE` / `NEXT_PAYMENT_DATE` / `LAST_CREDIT_PULL_DATE` | Payment and credit-check dates |

---

## 🧮 DAX Measures

| Measure | Purpose |
|---|---|
| `Total Loan Application` | Counts loan applications |
| `Total Funded Amount` | Sums the amount disbursed |
| `Total Amount Received` | Sums the amount repaid |
| `Average Interest Rate` | Averages the interest rate |
| `Average DTI Ratio` | Averages the borrower debt-to-income ratio |
| `Good Loan %` | Share of applications that are Fully Paid or Current |
| `Bad Loan %` | Share of applications that are Charged Off |
| `Good_vs_Bad_Loan` | Calculated column classifying each loan as a good or bad loan |

---

## 🛠️ Tools Used

- **Power BI Desktop:** data modelling, report design and visualisation
- **Power Query:** data cleaning and transformation
- **DAX:** KPI measures and the good-vs-bad loan classification
- **Microsoft Excel:** source dataset

---

## ✅ Conclusion

The dashboard gives the bank a clear, single view of its lending portfolio. It confirms a healthy overall position, with 86% good loans and repayments exceeding disbursements, while pointing to charged-off loans as the main source of loss. The link between higher interest rates, higher DTI and default suggests the bank should tighten approval criteria for high-DTI borrowers and monitor lower-grade loans more closely as application volumes keep growing.
