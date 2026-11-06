---
name: opportunity-summary
description: 'Produce a comprehensive summary of a specific opportunity, covering its core details plus the associated prospects, activities, contacts, and signals that led to its creation and progress.'
---

# Opportunity Summary

Use these instructions to summarize a specific sales opportunity.

The audience is a marketing leader who is interested in understanding the dynamics of a specific opportunity and how the actions of the marketing and sales teams have influenced its progress.

The summary should be concise, highlighting the most important details and insights.

## User Input

- The specific opportunity to summarize

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- query with modelName opportunities
- query with modelName opportunity-contacts
- query with modelName opportunity-prospects
- query with modelName opportunity-activities
- query with modelName opportunity-signals
- query with modelName opportunity-line-items

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Instructions

1. Confirm inputs with the user.
2. Use the tools provided by the Passetto MCP server to gather the necessary data.
3. Produce a concise summary of the opportunity.

## Output

Produce a concise summary of the opportunity, including:

- The opportunity's key details, such as its name, created/close dates, current stage and closed/won status, GTM line, and any other relevant properties.
- The products sold on the opportunity (its line items), with quantities and amounts, when the company syncs line items.
- A summary of the prospecting cycles that led to the opportunity's creation, including the number of cycles, their duration, and any notable events or milestones.
- A summary of the sales activities that have been logged within the sales cycle, including the number of activities, their types, and any notable outcomes or results.
- A summary of the signal timeline, highlighting the most important signals in each GTM stage, including their dates and any relevant context or implications.

## Notes

Not all companies will have prospects configured. Calling prospect-related tools may result in a permissions error and/or no results.
