---
name: analyze-marketing-influence
description: 'Analyze the influence of marketing on pipeline and revenue performance.'
---

# Analyze Marketing Influence

Use these instructions to analyze the influence of marketing on pipeline and revenue performance for a company in Passetto.

The audience is a marketing leader who needs to understand how marketing activities impact the company's pipeline and revenue performance. The results may be shared with marketing team members, sales leaders, and other leaders in the organization.

## User Input

- Time period for the analysis
- Specific GTM line(s) for the analysis

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName opportunities
- query with modelName opportunity-signals
- query with modelName opportunity-created-to-won-rate
- query with modelName opportunity-closed-to-won-rate
- query with modelName opportunity-average-won-amount
- query with modelName opportunity-average-created-to-won-days

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

In Passetto, marketing influence is measured by signals that represent an indivdual person's interaction with marketing activities and assets. Signals can be measured in two different contexts: raw signals and opportunity signals. Raw signals represent the interaction, and opportunity signals represent a signal that has been associated with an opportunity.

An opportunity signal will be categorized by a specific GTM Stage that represents the stage of the overall journey in which the interaction occurred. The GTM stages occur in the following order:

1. Engagement
2. Prospecting
3. Closing

An opportunity has summary properties that indicate if it has any signals (`has_signals`) and the total number of signals (`signal_full_path_count`). It also has properties for each GTM stage that indicate the presence and number of signals in that stage (`has_signals_<gtm_stage>` and `signal_<gtm_stage>_count`).

The `query` tool can be used to retrieve specific predefined measurements, such as "Opportunity Created to Won Rate", "Opportunity Closed to Won Rate", "Opportunity Average Won Amount", and "Opportunity Average Created to Won Days". These may be used in the analysis to understand the impact of marketing influence on opportunity metrics and outcomes.

The analysis should consider the impact of marketing on both pipeline creation (opportunities created) and revenue (opportunities won). Ultimately we care most about what helps to drive revenue.

## Instructions

1. Confirm inputs with the user.
2. Analyze top-level influence of marketing on opportunities by looking at which opportunities have signals and which do not. Identify any patterns where the presence of signals overall or within a specific GTM stage correlates with opportunity outcomes.
3. Drill down into specific opportunities and opportunity signals to understand the detailed impact of marketing activities on opportunity progression and revenue generation. Consider the GTM stages, signal types, channels, event types, form types, page URLs, and any other relevant attributes of the signals.
4. Summarize the findings and provide actionable insights on how marketing influence can be optimized to drive better opportunity outcomes and revenue generation.

## Output

The output should include a section of summarized findings, highlighting any key patterns, insights, and recommendations derived from the analysis. If opportunity-specific examples will illustrate the points, they should be included as well.

You may produce supporting visualizations, tables, or charts to help convey the findings more effectively. But you should not produce a standalone document or similar artifact.
