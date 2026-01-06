# COMSEC-Encryption-Lifecycle
Continuous monitoring + compliance automation for cryptographic key lifecycle risk (Power BI + Power Automate), aligned to NIST key management controls. 
# Cryptographic Control Monitoring & Compliance Automation (CCMCA)

## Overview
This project demonstrates a continuous monitoring approach for cryptographic key lifecycle risk.
It uses analytics to identify keys nearing expiration and automation to notify stakeholders.

## What it does
- Calculates **Days Until Expiration** and a risk category in Power BI
- Displays key lifecycle risk on a dashboard KPI
- Runs a **daily scheduled** Power Automate flow
- Sends an Outlook email when keys are within a defined expiration window (ex: <= 7 days)

## Architecture (High Level)
Dataset → Power BI (DAX measures + dashboard KPI) → Power Automate (daily recurrence) → Outlook notification

## Framework Alignment
- NIST SP 800-57 (Key Management lifecycle concepts)
- NIST SP 800-53 (SC-12, SC-13)
- Continuous Controls Monitoring (CCM)

## Project Status
Completed internal proof-of-concept for portfolio demonstration.
Not actively maintained.

## Disclaimer
All data is synthetic or redacted.
No operational systems, cryptographic material, or sensitive configurations are included
