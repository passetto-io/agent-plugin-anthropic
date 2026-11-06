---
name: kpi-prospect-qualified-count
description: 'Measure the KPI for count of prospects qualified in a period, analyze the trend over time, and explore the factors that influence prospect qualification.'
---

# KPI - Prospect Qualified Count

This KPI measures the count of prospects qualified in the period. Used to understand overall volume of prospects that are qualifying to opportunities.

## User Input

- The time interval for the analysis (month, quarter, year)
- The specific instance of the specified time interval (e.g. last month, this year, January 2026, etc.)
- Any additional filters or criteria

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName prospect-qualified-count
- query with modelName prospects
- query with modelName prospect-signals

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

Count the number of prospects where the `close_date` is in the specified time period, and `is_qualified` is true, applying any additional filters or criteria as needed. Using the `query` tool in Passetto, query the `prospect-qualified-count` model with the specified time period and any additional filters or criteria. The output is an integer that represents the total number of prospects qualified within the specified time period.

## Instructions

1. Confirm inputs with the user.
2. Query the `prospect-qualified-count` model for the specified time period and any additional filters or criteria to calculate the KPI value.
3. Analyze the trend over time by plotting the KPI for historical periods of the specified time interval. Prefer 8 or more data points, including the specified period. Look for patterns, seasonality, or any significant changes in volume.
4. Perform the exploratory analysis described in the Output section to understand the factors that influence the KPI.

## Output

Present the KPI value for the specified period, the trend analysis, and the exploratory analysis described below.

### What has triggered the creation of prospects?

Analyze the trigger types to which the qualified prospects are associated. The `prospect-qualified-count` model can be used, grouping by the `prospect_trigger_type_id` property.

Look to identify any trends or patterns in the triggers that lead to prospect qualification, including a change in the mix of trigger types over time.

### How long does it take to qualify prospects?

Analyze the duration from prospect creation to qualification. The `prospects` model includes a `stage_prospecting_duration` property that can be used to estimate the time spent in the prospecting stage prior to qualification.

Look to identify any trends or patterns in the time it takes for prospects to become qualified.

It may be helpful to look at differences in the prospecting stage duration between prospects that are qualified and those that are disqualified.

### What percentage of closed prospects are qualified?

Analyze the proportion of closed prospects that have been qualified. Use the `prospects` model to identify prospects with `is_closed` set to true and determine the percentage of those that have `is_qualified` set to true.

Look to identify any trends or patterns in the qualification rate of closed prospects over time. Are there any notable differences between trigger types?

### How many prospects have signals in the prospecting stage?

Analyze the percentage of prospects that have signals in the prospecting stage. Measure the mix of signal types and channels that drive these engagement stage signals.

Look to identify any trends or patterns in prospecting signal coverage over time.

### How long does it take for the first activity to be logged after prospect creation?

Analyze the time it takes for the first activity to be logged after a prospect is created. The `prospects` model includes a `new_to_first_activity_duration` property that represents the duration from prospect creation to the first logged activity.

Look to identify any trends or patterns in the time it takes for the first activity to be logged after prospect creation.

- Does this duration vary based on trigger types?
- Does the duration impact the likelihood of a prospect becoming qualified?
- Are there qualified prospects without any logged activities?
- What percentage of disqualified prospects have logged activities?

### Why are prospects being disqualified?

Analyze the reasons why prospects are being disqualified. Use the `prospects` model to identify prospects with `is_closed` set to true and `is_qualified` set to false, and examine the `disqualified_reason` property.

Look to identify any trends or patterns in the disqualification reasons over time. Are there specific trigger types or stages that are more prone to disqualification?

### What factors influence prospect qualification outcomes?

Identify whether any specific factors have a positive or negative influence on prospect outcomes (qualified, disqualified). Look at trigger type, engagement stage signal coverage, prospecting stage signal coverage, new-to-first-activity time, and prospect ownership (user, department, function).

## Notes

Not all users will have permissions to access prospect-related data. Calling prospect-related tools may result in a permissions error and/or no results.

When filtering by "New Business" GTM line, include prospects where `gtm_line_id` is 'UNCLASSIFIED'. Without more information, we assume a prospect likely represents new business.
