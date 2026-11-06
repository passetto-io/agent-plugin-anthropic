# Passetto

Passetto measures and analyzes go-to-market results. It connects to your CRM and marketing systems and attributes the signals that drive prospects and opportunities across the full go-to-market journey.

This plugin connects Claude to your Passetto account and adds skills for common analyses:

- **KPIs**: measure prospecting and closing KPIs for a period and compare them to the prior period.
- **Signal analysis**: analyze the engagement, prospecting, and closing signals behind prospects and opportunities.
- **Marketing influence**: understand how marketing activity influences pipeline and closed-won revenue.
- **Campaign and channel outcomes**: compare the signal volume, prospects, and pipeline produced by a specific campaign or channel.
- **Opportunity summaries**: summarize a single opportunity, including its contacts, activities, prospects, and signals.

## Install

In Claude Code, install the plugin from this repository:

```text
/plugin install passetto --marketplace passetto-io/agent-plugin-anthropic
```

On older versions of Claude Code, add the marketplace first, then install the plugin:

```bash
claude plugin marketplace add passetto-io/agent-plugin-anthropic
claude plugin install passetto@passetto
```

## Requirements

You need a Passetto account. When you first use the plugin, you're asked to sign in to Passetto to authorize access. The data you can see, and the settings you can change, follow the permissions of your Passetto user.

## What the plugin connects to

The plugin bundles one remote MCP server, `https://mcp.passetto.io/mcp`, operated by Passetto. All of the plugin's tools call that server, which reads your Passetto data and, for settings and job tools, updates it on your behalf. The plugin doesn't run any local commands, hooks, or scripts.

## Support

Visit [Passetto MCP support](https://mcp.passetto.io/support) or email [support@passetto.com](mailto:support@passetto.com). Use of the plugin is subject to the [Passetto MCP terms of service](https://mcp.passetto.io/terms). See the [Passetto privacy policy](https://www.passetto.com/privacy-policy) for how your data is handled.

This repository is published automatically from Passetto's source code, so pull requests here aren't merged. Send changes or problems to support instead.
