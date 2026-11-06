---
name: kpi-overview
description: 'Measure the full set of GTM Factory KPIs across the Prospecting and Closing stages of the GTM journey in a single dashboard, comparing the specified period to the prior period.'
---

# KPI - Overview

This prompt measures key metrics across the entire GTM journey (Engagement, Prospecting, and Closing) in a single dashboard, allowing the user to drill down into specific KPIs by asking follow-up questions.

## User Input

- Time period for the analysis (e.g. last month, last quarter, this year, last year, etc.)
- Any specific filters that should be applied to the analysis (e.g. GTM Line, Geography, etc.)

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName prospect-count
- query with modelName prospect-qualified-count
- query with modelName prospect-closed-to-qualified-rate
- query with modelName prospect-average-created-to-qualified-days
- query with modelName prospect-average-created-to-first-activity-days
- query with modelName opportunity-pipeline-created-count
- query with modelName opportunity-pipeline-created-amount
- query with modelName opportunity-closed-won-count
- query with modelName opportunity-closed-won-amount
- query with modelName opportunity-closed-to-won-rate
- query with modelName opportunity-average-won-amount
- query with modelName opportunity-average-created-to-won-days

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

This section defines each KPI and explains how it is calculated within the context of the GTM journey.

### Prospect Created Count

**GTM Stage:** Prospecting

Count the number of prospects with a `stage_date_new` falling within the measured period. Use the `query` tool with the `prospect-count` model.

### Prospect Qualified Count

**GTM Stage:** Prospecting

Count the number of prospects with a `close_date` falling within the measured period, `is_closed` is true, and `is_qualified` is true. Use the `query` tool with the `prospect-qualified-count` model.

### Prospect Closed to Qualified Rate

**GTM Stage:** Prospecting

Calculate the ratio of the number of prospects with a `close_date` falling within the measured period, `is_closed` is true, and `is_qualified` is true to the total number of prospects with a `close_date` falling within the measured period and `is_closed` is true. Use the `query` tool with the `prospect-closed-to-qualified-rate` model.

### Prospect Average Created to Qualified Days

**GTM Stage:** Prospecting

Calculate the average duration between the `stage_date_new` and `close_date` for prospects with a `close_date` falling within the measured period, `is_closed` is true, and `is_qualified` is true. Use the `query` tool with the `prospect-average-created-to-qualified-days` model.

### Prospect Average Created to First Activity Days

**GTM Stage:** Prospecting

Calculate the average duration between the `stage_date_new` and the `first_activity_date` for prospects with a `stage_date_new` falling within the measured period. Use the `query` tool with the `prospect-average-created-to-first-activity-days` model.

### Opportunity Pipeline Created Count

**GTM Stage:** Closing

Count the number of opportunities with a `record_created_date` falling within the measured period. Use the `query` tool with the `opportunity-pipeline-created-count` model.

### Opportunity Pipeline Created Amount

**GTM Stage:** Closing

Sum the `amount` of opportunities with a `record_created_date` falling within the measured period, converted to the company's primary currency. Use the `query` tool with the `opportunity-pipeline-created-amount` model.

### Opportunity Closed Won Count

**GTM Stage:** Closing

Count the number of opportunities with a `close_date` falling within the measured period, `is_closed` is true, and `is_won` is true. Use the `query` tool with the `opportunity-closed-won-count` model.

### Opportunity Closed Won Amount

**GTM Stage:** Closing

Sum the `amount` of opportunities with a `close_date` falling within the measured period, `is_closed` is true, and `is_won` is true, converted to the company's primary currency. Use the `query` tool with the `opportunity-closed-won-amount` model.

### Opportunity Closed to Won Rate

**GTM Stage:** Closing

Divide the number of opportunities with a `close_date` falling within the measured period, `is_closed` is true, and `is_won` is true by the total number of opportunities with a `close_date` falling within the measured period and `is_closed` is true. Use the `query` tool with the `opportunity-closed-to-won-rate` model.

### Opportunity Average Closed Won Amount

**GTM Stage:** Closing

Average the converted amount of opportunities with a `close_date` falling within the measured period, `is_closed` is true, and `is_won` is true. Use the `query` tool with the `opportunity-average-won-amount` model.

### Opportunity Average Created to Won Days

**GTM Stage:** Closing

Calculate the average difference in days between the `record_created_date` and `close_date` for opportunities with a `close_date` falling within the measured period, `is_closed` is true, and `is_won` is true. Use the `query` tool with the `opportunity-average-created-to-won-days` model.

## Instructions

1. Confirm inputs with the user.
2. Measure each KPI defined in the Concepts section for the specified period.
3. Measure the same KPIs for the prior period of the same length, so the specified period's results can be compared to the prior period.
4. Measure each KPI over roughly eight historical periods of the specified time interval, ending with the specified period, to support a trend chart.

## Output

For each KPI defined in the Concepts section, present:

- The KPI value for the specified period.
- How that value compares to the prior period (absolute and percentage change).
- A simple chart plotting the KPI value across the historical periods gathered in step 4 of the Instructions.

Group the KPIs by GTM Stage (Prospecting, Closing) so the dashboard reads as a single view across the GTM journey.

## Notes

When filtering by "New Business" GTM line, include prospects and opportunities where `gtm_line_id` is 'UNCLASSIFIED'. Without more information, we assume a prospect or opportunity likely represents new business.

Not all users will have permissions to access prospect-related or opportunity-related data. Calling related tools may result in a permissions error and/or no results.
