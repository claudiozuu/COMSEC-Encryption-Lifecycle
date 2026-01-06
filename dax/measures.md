# DAX Measures (Risk Logic)

***Days Until Expiration***
```DAX
Days Until Expiration =
DATEDIFF ( TODAY(), 'Clean Data'[Expire Date], DAY )

Expired Flag =
IF ( [Days Until Expiration] < 0, "Expired", "Active" )


Risk Category =
SWITCH(
TRUE(),
[Days Until Expiration] < 0, "Expired",
[Days Until Expiration] <= 7, "High",
[Days Until Expiration] <= 30, "Medium",
"Low"
)


Keys Expiring ≤ 7 Days =
CALCULATE(
COUNTROWS('Clean Data'),
[Days Until Expiration] <= 7
)


This is exactly what recruiters want: **clear logic + business thresholds + alert measure**.

---

# 3) Add screenshots (with evidence)

Upload these to `/docs`:
- `raw_data.png` (you already have)
- `clean_data.png`
- `dashboard_redacted.png` (Power BI dashboard showing the KPI card and table)
- `flow_redacted.png` (Power Automate flow screenshot)

Then in your **README**, add:

```md
## Evidence
### Raw → Clean Data
![Raw Data](docs/raw_data.png)
![Clean Data](docs/clean_data.png)

### Dashboard & Alerts
![Dashboard](docs/dashboard_redacted.png)

### Automation Flow
![Power Automate Flow](docs/flow_redacted.png)
