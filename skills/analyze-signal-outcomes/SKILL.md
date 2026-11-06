---
name: analyze-signal-outcomes
description: 'Measure the outcomes of raw signals, in terms of how they end up attributed to pipeline and revenue.'
---

# Analyze Signal Outcomes

The objective is to analyze how raw signals end up attributed to pipeline and revenue. Some signals will end up part of one or more opportunity journeys, and others will not. We want to understand the dynamics that determine which signals contribute to pipeline and revenue and which do not.

## User Input

- Time period for the analysis (e.g., last 24 months)
- Specific GTM line(s) to focus on (e.g., New Business)
- Specific signal types, channels, or campaigns to focus on

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName signals
- query with modelName opportunity-signals
- query with modelName opportunities

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

Common groupings of channel IDs for analysis are:

- Organic: ORGANIC_SEARCH, ORGANIC_SOCIAL, DIRECT, WEB_REFERRAL, GENERATIVE_AI
- Paid: PAID_SEARCH, PAID_SOCIAL, PAID_EMAIL, PAID_VIDEO, PAID_PRINT, PAID_OTHER, DISPLAY, CONNECTED_TV_ADVERTISING, OUT_OF_HOME_ADVERTISING, TELEVISION_ADVERTISING

Use the `signals` and `opportunity-signals` models to extract and analyze information about raw signals and their opportunity attribution. A raw signal from the `signals` model may be attributed to zero, one, or multiple opportunities, and the attribution details can be found in the `opportunity-signals` model.

## Instructions

1. Confirm inputs with the user.
2. For the given time period and any specific GTM line(s) selected, measure the raw signals for each channel, the count and value of opportunities attributed to those signals, and the count and value of the attributed opportunities that are closed as won.
3. Analyze the efficiency of raw signals by comparing the number of raw signals to the attributed impact on pipeline and revenue. Identify which signals are most effective at driving opportunities and revenue, and which are underperforming.

Consider the `attribution_linear_full` and `amount_linear_full_converted` properties from the opportunity signals, as well as the `amount_converted` property from the opportunities. In addition to any user-provided filters, make sure to filter the opportunity-signals queries by `gtm_stage_id` = "ENGAGEMENT" to focus on engagement stage opportunity signals.
