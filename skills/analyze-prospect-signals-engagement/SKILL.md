---
name: analyze-prospect-signals-engagement
description: 'Identify engagement-stage signal patterns that precede the creation of prospects, to inform marketing strategy.'
---

# Analyze Prospect Signals (Engagement Stage)

The objective is to determine patterns of engagement that lead to the creation of prospects. The analysis leverages prospect signals to identify interactions that occur in the Engagement stage for each prospect. The idea is to uncover signal types, channels, and/or campaigns that are commonly seen in the journey to a prospect, so the marketing team can optimize their strategies and focus on the most effective engagement tactics.

## User Input

- Time frame (e.g. last 12 months)
- Prospect trigger type(s) (e.g. WEB_FORM)
- Prospect GTM line(s) (e.g. NEW_BUSINESS)

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName prospects
- query with modelName prospect-signals

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

Prospect signals in the Engagement GTM stage occur prior to the prospect being created. It is likely that some signal types, channels, and/or campaigns are more common and influential in driving prospects of certain trigger types. For example, a "web form" prospect may be preceded by specific types of website interactions or marketing campaigns that indicate a higher likelihood of conversion. For prospects within the specified criteria (time frame, trigger type, GTM line), we summarize facts about the engagement signals that lead up to the creation of the prospect, and then perform an analysis to identify patterns and trends that can inform future marketing strategies.

The prospects model exposes `prospect_trigger_type__name` and `gtm_line__name` (filterable via `prospect_trigger_type_id` and `gtm_line_id`) to scope prospects to the specified criteria. The prospect-signals model should be filtered by `gtm_stage_id` = "ENGAGEMENT" to focus on engagement signals that occur prior to the creation of a prospect, and by prospect related properties (e.g. `prospect_record_id`, `prospect_trigger_type_id`, etc.) to scope results to the prospects identified above.

## Instructions

1. Confirm inputs with the user.
2. Query the prospects model to identify prospects within the specified criteria (time frame, trigger type, GTM line, etc.).
3. Query the prospect-signals model, filtered to `gtm_stage_id` = "ENGAGEMENT" and any prospect filtering criteria. Group and aggregate the signals by prospect and relevant dimensions such as signal type, channel, and campaign to facilitate analysis.
4. Aggregate and analyze the retrieved signals to identify patterns and trends that precede the creation of prospects.
5. Summarize the findings and provide actionable insights for the marketing team.

## Output

A summary of engagement signals that are most commonly associated with the creation of prospects, along with any identified patterns or trends. Include tables and/or charts that highlight the key findings and actionable insights for the marketing team.

## Notes

Not all users will have permissions to access prospect-related data. Calling prospect-related tools may result in a permissions error and/or no results.
