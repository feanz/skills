---
name: azure-prod-performance-report
description: Create a markdown report of significant performance issues in the last week in production azure 
---

## Context

- Use Azure `az` cli to get data on the current production environment 
- The production environment is in a subscription with production in its name\
- We use azure container services to host application
- We use azure function apps for event processing
- We use SQL azure for all databases
- We use Azure service bus for events
- All services are connected to a single application insights instance in production 
- The report should only focus on the last week

## Your task

Review the most significant performance issues in the production subscription.  Focus on the last week. Look at the most significant slow endpoints via application insights and slow performance of SQL azure databases.  Provide any details you can on the underlying cause of the performance issue. Highlight any common issues or correlations you can see in the data. 

Output the report to a markdown file. 