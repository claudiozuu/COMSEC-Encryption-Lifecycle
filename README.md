# COMSEC Encryption Automation (Power BI + Power Automate)

This project is an **automated COMSEC key-expiration monitoring + alerting workflow** built with **Power BI** and **Power Automate**. It calculates **Days Until Expiration**, flags **Expired** items, assigns a **Risk Category**, and then runs a **scheduled query** against the Power BI dataset. If any keys are within the alert window (ex: **≤ 7 days**), the flow automatically sends an email notification—no manual checks required.

> **Purpose:** Reduce expired/at-risk COMSEC material by turning the tracker into an automated, repeatable alert process that supports inspections, continuity, and commander-level visibility.

---

## Features

![Workflow Overview](images/workflow_overview.png)

### **1. Expiration Tracking (Power BI Calculations)**
- Calculates **Days Until Expiration** from the key’s **EXPIRE DATE**.
- Generates an **Expired Flag** (Expired vs Active).
- Assigns a **Risk Category** (Expired / High / Medium / Low) based on remaining days.

### **2. Scheduled Automation (Power Automate)**
- Runs on a daily schedule (ex: **1500 HST**).
- Queries the Power BI dataset for keys within a defined alert threshold (ex: **≤ 7 days**).
- Evaluates if any rows are returned; if yes, sends an email alert.

### **3. Targeted Notifications**
- Only emails when there’s something to action.
- Prevents “noise” and unnecessary inbox spam.

---

## Screenshots

### Power Automate Flow (End-to-End)
![Power Automate Flow](images/workflow_overview.png)

### Recurrence Schedule
![Recurrence Schedule](images/recurrence_schedule.png)

### Run a Query Against a Dataset (Power BI)
![Dataset Query](images/dataset_query.png)

### Condition Expression (Only Email if Results Exist)
![Condition Expression](images/condition_expression.png)

### Code View (JSON) – Dataset Query
![Query JSON](images/query_json.png)

### Power BI Calculated Columns (DAX)
**Days Until Expiration**
![Days Until Expiration](images/dax_days_until_expiration.png)

**Expired Flag**
![Expired Flag](images/dax_expired_flag.png)

**Risk Category**
![Risk Category](images/dax_risk_category.png)

---

## How It Works (Workflow Overview)

1. **Recurrence Trigger** – runs on a schedule (daily / hourly as desired).  
2. **Run a query against a dataset** – executes a DAX query against the Power BI dataset.  
3. **Condition** – checks whether the query returned rows (meaning keys are within the alert threshold).  
4. **Send an email (V2)** – sends an alert email when action is required.

---

## Key Components

| Component | Purpose |
|----------|---------|
| **Power BI Dataset** | Hosts COMSEC tracker + calculated columns |
| **DAX Calculated Columns** | Days until expiration, expired flag, risk category |
| **Power Automate – Recurrence** | Scheduled execution |
| **Power Automate – Run a query against a dataset** | Pulls only relevant at-risk keys |
| **Power Automate – Condition** | Only send email if rows exist |
| **Send Email (V2)** | Notification delivery |

---

## Power BI: DAX Calculations (As Implemented)

### 1) Days Until Expiration
```DAX
Days Until Expiration =
DATEDIFF(TODAY(), 'HHC COMSEC'[EXPIRE DATE], DAY)
