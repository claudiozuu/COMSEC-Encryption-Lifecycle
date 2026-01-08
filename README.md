# COMSEC Encryption Automation (Power BI + Power Automate)

This project is an **automated COMSEC key-expiration monitoring and alerting system** built using **Power BI** and **Power Automate**. It takes raw COMSEC tracker data, cleans and standardizes it, calculates expiration risk using DAX, and then runs a scheduled query against the published Power BI dataset. If any keys are expiring within a defined threshold (ex: **≤ 7 days**), the flow automatically sends an **Outlook email alert**—no manual checks required.

> **Purpose:** Reduce expired/at-risk COMSEC keys by turning the tracker into an automated, repeatable alert workflow that supports continuity, readiness, and leadership visibility.

---

## Features

![Workflow Diagram](images/workflow_overview.png)

### **1. Raw Data → Clean Data (Power Query)**
- Imports COMSEC tracker data (Excel/CSV export).
- Standardizes column types (especially **EXPIRE DATE**).
- Removes inconsistencies (nulls/format issues) to ensure reliable automation.

### **2. Power BI Expiration Intelligence (DAX)**
- **Days Until Expiration** (date math from TODAY())  
- **Expired Flag** (Expired vs Active)  
- **Risk Category** (Expired / High / Medium / Low)

### **3. Power Automate Scheduled Monitoring**
- Runs on a daily **Recurrence schedule** (ex: 1500 HST).
- Executes **Run a query against a dataset** using DAX to pull only at-risk rows.

### **4. Automatic Outlook Email Alert**
- Uses a **Condition** to check whether any at-risk keys were returned.
- If **True**, sends an email notification with action required.
- If **False**, sends nothing (reduces inbox noise).

---

## How It Works (Workflow Overview)

1. **Raw COMSEC Data (Excel/CSV Export)** – initial tracker data source.  
2. **Data Cleaning + Standardization (Power Query)** – prepares data for accurate calculations and automation.  
3. **Power BI Model + DAX Calculations** – creates expiration metrics and risk labels.  
4. **Publish to Power BI Service** – creates the dataset used by automation.  
5. **Power Automate Recurrence** – runs the workflow on schedule.  
6. **Run a Query Against a Dataset** – filters keys expiring within threshold (ex: ≤ 7 days).  
7. **Condition** – checks if the query returned rows.  
8. **Outlook Email** – sends alert if action is required.

---

## Key Components

| Component | Purpose |
|----------|---------|
| **Raw Excel/CSV Export** | Source COMSEC tracker data |
| **Power Query** | Clean + standardize data types/format |
| **Power BI Dataset** | Hosts the model + calculations |
| **DAX Calculations** | Days Until Expiration, Expired Flag, Risk Category |
| **Power Automate (Recurrence)** | Schedules daily automation runs |
| **Run a query against a dataset** | Pulls only at-risk keys from the dataset |
| **Condition** | Only emails when results exist |
| **Outlook (Send email V2)** | Sends the final alert |

---

## Screenshots

### Power Automate – Recurrence Schedule
![Recurrence Schedule](images/recurrence_schedule.png)

### Power Automate – Run a Query Against a Dataset (DAX Filter)
![Run a Query](images/run_query_dataset.png)

### Power Automate – Condition Expression (Only Email if Rows Exist)
![Condition Expression](images/condition_expression_part_1.png)  
![Condition Expression (Detail)](images/condition_expression_part_2.png)

### Power BI – Days Until Expiration
![Days Until Expiration](images/dax_days_until_expiration.png)

### Power BI – Expired Flag
![Expired Flag](images/dax_expired_flag.png)

### Power BI – Risk Category
![Risk Category](images/dax_risk_category.png)

### Power BI – Report Visuals / Dashboard View
![Report Visuals](images/report_visuals.png)

---

## Power BI: DAX Calculations

### **Days Until Expiration**
```DAX
Days Until Expiration =
DATEDIFF(TODAY(), 'HHC COMSEC'[EXPIRE DATE], DAY)
