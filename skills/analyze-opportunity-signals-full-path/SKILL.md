---
name: analyze-opportunity-signals-full-path
description: 'Analyze how opportunity signals across all GTM stages are attributed to pipeline and revenue.'
---

# Analyze Opportunity Signals (Full Path)

The objective is to measure how signals are attributed to pipeline and revenue.

## User Input

- Time period for the analysis
- Specific GTM line(s) to focus on

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName opportunity-signals
- query with modelName opportunities

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

Use the opportunity-signals model to measure signals that are attributed to opportunities. The `attribution_linear_full` property measures the share of the opportunity count that was attributed to the individual signal. The `amount_linear_full` property measures the share of the opportunity amount that was attributed to the individual signal.

Signals in an opportunity journey may occur in one of three GTM stages: Engagement -> Prospecting -> Closing.

## Instructions

1. Confirm inputs with the user.
2. For pipeline, measure opportunity signals associated with opportunities that were created within the time period, filtered by GTM line if specified.
3. For revenue, measure opportunity signals associated with opportunities that were closed as won with a close date within the time period, filtered by GTM line if specified.

When measuring, look at signal types, channels, and campaigns to understand which marketing efforts are influencing the most pipeline and revenue, and identify any that are underperforming.

## Output

Output tables and charts to visualize the contribution of different signal types, channels, and campaigns to pipeline and revenue, highlighting both top performers and underperformers.
