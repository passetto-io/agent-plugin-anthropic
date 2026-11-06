---
name: analyze-opportunity-signals-engagement
description: 'Analyze if (and how) pre-opportunity engagement patterns are changing over time.'
---

# Analyze Opportunity Signals (Engagement Stage)

The objective is to understand if (and how) pre-opportunity engagement patterns are changing over time.

## User Input

- Time period for the analysis
- Specific GTM line(s) to focus on

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName opportunity-signals
- query with modelName opportunities

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

Signals in an opportunity journey may occur in one of three GTM stages: Engagement -> Prospecting -> Closing. The Engagement stage captures early interactions and touchpoints that occur before an opportunity is formally created. The hypothesis is that changes in engagement signals can provide early indicators of shifts in opportunity dynamics.

The opportunity-signals query model measures signals that are attributed to opportunities. Filter on `gtm_stage_id` = "ENGAGEMENT" to focus on engagement stage signals only. The `attribution_linear_full` property measures the share of the opportunity count (a fraction of 1) that was attributed to the individual signal. The `amount_linear_full` property measures the share of the opportunity amount (a fraction of the total amount) that was attributed to the individual signal.

## Instructions

1. Confirm inputs with the user.
2. Look at opportunity signals in the Engagement stage for opportunities with a created date within the time period, filtered by GTM line if specified. Focus on changes in the composition of signal types, channels, and campaigns that are seen in the Engagement stage for these opportunities.
3. Compare the current period to the prior period to identify trends and shifts in engagement patterns. Consider the efficiency of signals, in terms of raw touchpoints versus attributed impact.
4. If there are signal types, channels, or campaigns that increased or decreased their influence by a meaningful amount between the current and prior periods, highlight these changes.

## Output

Output tables and charts to visualize the contribution of different signal types, channels, and campaigns to pipeline and revenue, highlighting both top performers and underperformers.
