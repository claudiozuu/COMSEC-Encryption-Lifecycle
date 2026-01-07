# Step 4 — Automated Notifications

## Objective
Automate notification when encryption keys approach expiration.

## Automation Logic
- Daily recurrence (1430 HST or your preffered Time zone)

## Query Power BI dataset:
- Select Power BI
- Run a query against a dataset
- Choose your workspace where you keep the table
- Chose your dataset
- Input Query text 
- If expiring keys > 0, send email notification
- Prevent alert fatigue by limiting to once per day

## Key Measures for Power Automate 
- Query text
- Condition: Function Expression

## Outcome
Sustained compliance monitoring without continuous human intervention.
