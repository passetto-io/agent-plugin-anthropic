---
name: kpi-prospect-created-count
description: 'Measure the KPI for count of prospects created in a period, analyze the trend over time, and explore the factors that influence prospect creation volume.'
---

# KPI - Prospect Created Count

This KPI measures the count of prospects created in the period. Used to understand overall volume of prospects created.

## User Input

- The time interval for the analysis (month, quarter, year)
- The specific instance of the specified time interval (e.g. last month, this year, January 2026, etc.)
- Any additional filters or criteria

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName prospect-count
- query with modelName prospects
- query with modelName prospect-signals

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

Count the number of prospects where the `stage_date_new` is in the specified time period, applying any additional filters or criteria as needed. Using the `query` tool in Passetto, query the `prospect-count` model with the specified time period and any additional filters or criteria. The output is an integer that represents the total number of prospects created within the specified time period.

## Instructions

1. Confirm inputs with the user.
2. Query the `prospect-count` model for the specified time period and any additional filters or criteria to calculate the KPI value.
3. Analyze the trend over time by plotting the KPI for historical periods of the specified time interval. Prefer 8 or more data points, including the specified period. Look for patterns, seasonality, or any significant changes in volume.
4. Perform the exploratory analysis described in the Output section to understand the factors that influence the KPI.

## Output

Present the KPI value for the specified period, the trend analysis, and the exploratory analysis described below.

### What has triggered the creation of prospects?

Analyze the trigger types to which the created prospects are associated. The `prospect-count` model can be used, grouping by the `prospect_trigger_type_id` property.

Look to identify any trends or patterns in the triggers that lead to prospect creation, including a change in the mix of trigger types over time.

### How many prospects have signals in the engagement stage?

Analyze the percentage of prospects that have signals in the engagement stage. Measure the mix of signal types and channels that drive these engagement stage signals.

Use the `stage_engagement_last_touch` property to identify and analyze the last signal that occurred in the engagement stage for each prospect.

Look to identify any trends or patterns in engagement signal coverage or last engagement signal over time.

### How long is the engagement stage prior to prospect creation?

Analyze how long people are typically in the "Engagement" stage prior to the creation of a prospect. The `prospects` model includes a `stage_engagement_duration` property that represents the number of seconds spent in the engagement stage for each prospect. Consider the difference between prospects that have signals in the engagement stage, and those that do not.

Look to identify any trends or patterns in the duration of the engagement stage prior to prospect creation.

## Notes

Not all users will have permissions to access prospect-related data. Calling prospect-related tools may result in a permissions error and/or no results.

When filtering by "New Business" GTM line, include prospects where `gtm_line_id` is 'UNCLASSIFIED'. Without more information, we assume a prospect likely represents new business.
