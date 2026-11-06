---
name: campaign-outcomes-analysis
description: 'Analyze the impact of a specific marketing campaign, in terms of signal volume, prospect influence, and opportunity influence.'
---

# Campaign Outcomes Analysis

The objective is to understand the impact of a specific marketing campaign. This is measured based on signals, representing how the campaign has driven engagement with the target audience.

## User Input

- The specific campaign (`campaign_name`) to analyze

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName signals
- query with modelName prospect-signals
- query with modelName opportunity-signals

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

A signal represents an interaction that a person has with the brand. Signals can be page views, event registration/attendance, and other forms of engagement that indicate interest or involvement with the campaign.

A signal record represents the engagement that occurred. Attribution calculations connect the signal to prospects and opportunities to indicate that the signal contributed to the GTM journey before or during the prospecting or closing stages.

Each signal has a signal type (`signal_type_id`) to represent the type of interaction that occurred. It may also have information about the channel (`channel_id`) and the campaign (`campaign_name`) that drove the interaction.

- Every signal will have a signal type.
- Not all signals will have a channel. When missing, the `channel_id` will be "UNCLASSIFIED". When channel is missing, this usually indicates that signal data is incomplete. This suggests an opportunity to improve marketing execution or tracking.
- Not all signals will have a campaign. When missing, the `campaign_name` will be empty. It is expected that certain signal types and channels may not always be associated with a campaign, since some interactions may occur independently of specific marketing campaigns.

## Instructions

1. Confirm with the user which campaign they want to analyze.
2. Measure the total count of signals collected for the campaign, and the distribution of that count over time.
3. Measure the distribution of signals by signal type, including the total count and distribution over time for each signal type.
   - For page view signals, measure the top viewed pages to understand which content is attracting the most attention.
   - For form submit signals, measure the top submitted forms to understand which forms are generating the most engagement. Include the pages where the forms are located.
4. Measure the distribution of signals by channel, including the total count and distribution over time for each channel. If there are significant numbers of signals without a channel, investigate why the channel information is missing and consider ways to improve tracking.
5. Using the `prospect-signals` model, measure if the signals have influenced any prospects:
   - Count the total number of influenced prospects.
   - Analyze the distribution of prospect signals by GTM stage to understand if the influence occurs before the prospecting cycle ("Engagement" stage) or during the prospecting cycle ("Prospecting" stage).
   - Analyze if signals are attributed to the "first touch" (`is_first_touch`) journey milestone.
6. Using the `opportunity-signals` model, measure if the signals have influenced any opportunities:
   - Count the total number of influenced opportunities.
   - Analyze the distribution of opportunity signals by GTM stage to understand if the influence occurs before the closing cycle ("Engagement" or "Prospecting" stages) or during the closing cycle ("Closing" stage).
   - Analyze if signals are attributed to the "first touch" (`is_first_touch`) journey milestone.
   - Calculate the total attribution amount and count for influenced opportunities.
7. Compare this campaign to other campaigns on total count of signals, total attribution amount for influenced opportunities, total count of influenced opportunities, and total count of influenced prospects. Use the same signal date time period for all campaigns to ensure a fair comparison.

## Output

A summary of the campaign's performance across signal volume, prospect influence, and opportunity influence, including how it compares to other campaigns on the same key metrics. Include tables and/or charts that highlight the key findings.

## Notes

Not all users will have permissions to access prospect-related data. Calling prospect-related tools may result in a permissions error and/or no results.
