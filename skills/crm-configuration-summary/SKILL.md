---
name: crm-configuration-summary
description: 'Summarize CRM configuration and a sample of the relevant data.'
---

# CRM Configuration Summary

Use these instructions to summarize the CRM configuration for a company in Passetto.

The audience is a marketing leader who is interested in understanding how their account in Passetto is configured and how the data is structured. The summary should be concise, clear, and focused on the most relevant information for a marketing leader and their team of marketers and operations professionals. The summary should be written in a way that is easy to understand for someone who may not be familiar with the technical details of the Passetto platform.

## User Input

- Time period for the analysis
- Any specific GTM line(s) to focus on

## Tools

Use the following tools in the Passetto MCP server to gather data for the analysis:

- read_company_settings
- read_opportunity_gtm_line_settings
- list_segment_settings
- read_segment_setting
- query
- model_metadata

Before gathering data, call list_annotations for the company, filtered to the analysis period (relevant_from LTE its last day and relevant_until GTE its first day), and account for those annotations (process changes, known data issues) when interpreting the results.

## Concepts

When working with GTM Stage, order them as follows: "Engagement", "Prospecting", "Closing".

## Instructions

1. Confirm the inputs with the user.
2. Gather the necessary data using the tools provided by the Passetto MCP server. The most important tools are listed in the Tools section below. You may use other Passetto tools as needed.
3. Summarize the CRM configuration and the sample of core data for the company, focusing on the most relevant information for a marketing leader and their team.

## Output

Produce a concise summary of the current configuration and data, constructing a document that can be shared with team members. If branding guidelines are available, use them.

Do not include any interpretations or recommendations, just summarize the configuration and data. The summary should include the sections detailed below.

### Company Settings

Summarize the company-level settings, covering which CRM is connected, the reporting currency, the attribution path, the CRM opportunity properties mapped to Passetto properties, and which calculations are enabled. Do not include any settings related to prospecting.

If a property mapping setting is not mapped, no need to mention it.

### Opportunity GTM Line

Summarize the rules that are used to classify opportunities by GTM line. If the rules reference a record id, such as opportunity_record_id, attempt to retrieve the human-readable name for that record and include it in the summary.

Summarize opportunity counts for the relevant GTM lines for the specified analysis time period. Include a top-level count as well as a monthly breakdown. If the user has specific GTM lines of interest, focus the summary on those lines.

If there are many opportunities in the "UNCLASSIFIED" GTM line, you may attempt to determine why these are not classified.

### Segmentation

Summarize the settings for segmentation. Each entity may have more than one segment setting defined, and each segment setting may define multiple segment groupings.

For each segment setting, summarize the following:

- The segment setting name and description.
- The entity to which the segment is associated.
- A summary of the rules that drive each individual segment grouping.

Summarize counts of how the entity records are distributed across segment groupings.

If there are segment settings for the account entity, also summarize counts of how opportunities are distributed across the account segments.

The following segment names will correspond to a specific property on the related entity:

- market -> market_segment
- geographic -> geographic_segment
- industry -> industry_segment

Any other segment names will be considered custom segments and will be defined in the `segments` property on the entity. The segment grouping value for that segment will be represented as "{custom_segment_name}:{custom_segment_grouping}".

If there are many records in the "UNCLASSIFIED" segment grouping, you may attempt to suggest why these are not classified.

### Opportunity Contacts

Measure the opportunity contact coverage, detailing the percentage of opportunities that have at least one contact associated. Use the `contact_count` property on the opportunity entity to determine the number of contacts associated with each opportunity.

- Measure the percentage of opportunities that have at least one contact associated.
- If the analysis is relevant to more than one GTM line, break this out by opportunity GTM line to provide insight into how contact coverage varies across different GTM lines.
- Review coverage trends over the specified analysis period to identify any patterns or changes in contact coverage over time based on opportunity created date.
- Measure average and/or median to understand the typical level of contact coverage across opportunities.

### Opportunity Signals

Measure the opportunity signal coverage, detailing the percentage of opportunities that have at least one signal associated. Use the `signal_full_path_count` property on the opportunity entity to determine the number of signals associated with each opportunity. Also look at the `signal_{gtm_stage}_count` properties to determine the number of signals associated with each GTM stage for each opportunity.

- Measure the percentage of opportunities that have at least one signal associated.
- If the analysis is relevant to more than one GTM line, break this out by opportunity GTM line to provide insight into how signal coverage varies across different GTM lines.
- Review coverage trends over the specified analysis period to identify any patterns or changes in signal coverage over time based on opportunity created date.
- Measure average and/or median to understand the typical level of signal coverage across opportunities.

Measure the distribution of opportunity signals by key dimensions, producing separate summaries for each dimension. Focus on signals associated with opportunities created within the analysis period.

- Signal Type
- Channel
- Source Entity
- GTM Stage

### Opportunity Activities

Measure the opportunity activity coverage, detailing the percentage of opportunities that have at least one activity associated. Use the `activity_count` property on the opportunity entity to determine the number of activities associated with each opportunity.

- Measure the percentage of opportunities that have at least one activity associated.
- If the analysis is relevant to more than one GTM line, break this out by opportunity GTM line to provide insight into how activity coverage varies across different GTM lines.
- Review coverage trends over the specified analysis period to identify any patterns or changes in activity coverage over time based on opportunity created date.
- Measure average and/or median to understand the typical level of activity coverage across opportunities.

### Signals

Measure the distribution of signals by key dimensions, producing separate summaries for each dimension.

- Signal Type
- Channel
- Source Entity

Focus on signals with a signal date within the analysis period.
