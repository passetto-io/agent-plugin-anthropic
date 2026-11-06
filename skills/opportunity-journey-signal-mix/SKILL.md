---
name: opportunity-journey-signal-mix
description: 'Analyze the mix of signal types and channels within each GTM stage of the opportunity journey.'
---

# Opportunity Journey Signal Mix

The objective is to understand how different signal types and channels contribute to the overall opportunity journey. Each signal within an opportunity journey falls into one of three GTM stages: Engagement, Prospecting, Closing. We want to know which signal types and channels are most common at each stage.

## User Input

- Time period for the analysis (e.g., last 30 days, last quarter)
- GTM Line(s) to focus on (e.g., New Business, Expansion, Renewal)
- Opportunity outcome (Closed Won, Closed Lost, All Closed)

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName opportunities
- query with modelName opportunity-signals
- query with modelName signals
- read_company_settings

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

A signal is associated to an opportunity based on the contacts associated with the opportunity. Depending on the `attribution_path` setting for the company, contacts are identified either by direct contact->opportunity association, or by contact->account association for the account associated to the opportunity.

The GTM stage represents where in the opportunity journey the signal occurred:

- Engagement: The signal occurred before a prospect or opportunity was created.
- Prospecting: The signal occurred during a prospecting cycle before the opportunity is created.
- Closing: The signal occurred after the opportunity was created and before the opportunity is closed.

By looking at the mix of signal types and channels within a stage, and then the mix of stages for each signal type and channel, we can identify patterns and trends that inform GTM strategy and resource allocation.

## Instructions

1. Confirm inputs with the user.
2. Read the company settings to understand the attribution path and other relevant configurations.
3. Query the opportunities model to get the relevant opportunities based on the user input.
4. Query the opportunity-signals model to get the signals associated with the opportunities.
5. Analyze the mix of GTM stages, signal types, and channels to identify patterns and trends.
6. Summarize the findings into a concise set of charts and visualizations, aligning with the instructions in the Output section.

Filter opportunities and opportunity signals based on GTM Line, Is Closed, Is Won, and Close Date.

Never include open opportunities (Is Closed = false) because the "Closing" GTM stage is still in progress.

## Output

Use these guidelines to direct how to present the findings to the user.

### Summary Metrics

Calculate and display the following top-level metrics based on the provided filter context:

- Opportunities: Count of opportunities relevant to the analysis.
- Signals per opportunity: Average and median count of signals per opportunity.
- Share of signals during Engagement Stage: Percent of signals that occur in the Engagement stage.
- Opportunities with a signal: Percent of opportunities with signals.
- Most influential channel: The most influential channel by opportunity count. Do not consider "Unclassified".
- Most influential campaign: The most influential campaign by opportunity count. Do not consider empty values.

### Signal Types by GTM Stage

Visualize the distribution of signal types across the different GTM stages. Generate a table that includes counts and percentages to highlight the relative importance of each signal type within each stage. Orient the table with rows for each signal type, and columns for each GTM stage. In the far-right column of each row, use a stacked bar to visually represent the proportions within each stage.

For page view signals, measure the top pages in each GTM stage.

For form submission signals, measure the top forms in each GTM stage.

For event signals, measure the top events in each GTM stage.

### Channels by GTM Stage

Visualize the distribution of channels across the different GTM stages. Generate a table that includes counts and percentages to highlight the relative importance of each channel within each GTM stage. Orient the table with rows for each channel, and columns for each GTM stage. In the far-right column of each row, use a stacked bar to visually represent the proportions within each stage.

### Campaigns by GTM Stage

Measure the most influential campaigns that are driving the signal types and channels across the different GTM stages. Generate a table showing the top campaigns (up to 10) that are driving the signals in each GTM stage. For each listed campaign, measure the count of signals, and the percentage of all relevant signals. Also include the top signal type and top channel for that campaign.

### Milestone Signals

Analyze the signals that represent specific journey milestones:

- First Touch
- Engagement Stage Last Touch
- Prospecting Stage Last Touch

Produce visualizations that show the mix of signal types and campaigns for signals representing these specific milestones.

### Success Path Patterns

Summarize some of the top-performing opportunity journeys, highlighting the key signals, channels, and campaigns that contributed to their success. Look for recurring patterns and common sequences that appear across multiple successful opportunities, including common patterns within each GTM stage.
