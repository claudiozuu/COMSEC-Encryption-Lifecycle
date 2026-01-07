# Step 4 — Automated Notifications

## Objective
Automate notification when encryption keys approach expiration.

## Automation Logic
- Daily recurrence (1430 HST or your preffered Time zone)
- Query Power BI dataset:
      1. Select Power BI
      2. Run a query against a dataset
      3. Choose your workspace where you keep the table
      4. Chose your dataset
      5. Input Query text 
- If expiring keys > 0, send email notification
- Prevent alert fatigue by limiting to once per day

## Key Measures for Power Automate 
- Query text
- Condition: Function Expression

## Outcome
Sustained compliance monitoring without continuous human intervention.
