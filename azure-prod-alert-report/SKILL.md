---
name: azure-prod-alert-report
description: Create a markdown report of significant alerts in the last week in production azure 
---

## Context

- Use Azure `az` cli to get data on the current production environment 
- The production environment is in a subscription with production in its name\
- We use azure built in alerts to manage all monitoring
- The report should only focus on the last week

## Your task

Review the alerts that have been trigger in azure in the production subscription in the last week.  Only look at alerts that relate to resources that are in the production subscription.  Produce a report on the significant alerts that have been triggered.  Detail the cause of the alert and any context information on underlying causes. Highlight common issues or changes that should be made to alert thresholds. 

Output the report to a markdown file. 