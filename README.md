# InvestIQ for Claude

Research Indian listed companies (NSE/BSE) from Claude using [InvestIQ](https://investiq.live)'s saved multi-model intrinsic valuations. The plugin connects Claude to InvestIQ's remote MCP server and adds two skills that teach Claude how to use it well.

## What it does

- Search companies and read fundamentals, ratios and analyst sentiment.
- Read saved composite valuations built from five models: DCF, DDM, residual income, earnings power value and sector-relative comps.
- Screen the market by sector, margin of safety and confidence.
- Run three built-in strategies: value investing, growth + undervaluation, deep value.
- Check how old the underlying data is before trusting it.

## Install

```
/plugin marketplace add atishay1743/investiq-claude-plugin
/plugin install investiq@investiq
```

On first use Claude opens an InvestIQ sign-in page. Approve read-only access. Website login cookies and Google tokens are never shared with Claude.

## Try it

- "Find Infosys on NSE and explain its latest saved valuation. How old is the data?"
- "List five Technology stocks with margin of safety above 20% and confidence above 60."
- "What strategies does InvestIQ offer? Show Value Investing results."

## What the plugin runs, sends and fetches

- **No local code.** Nothing executes on your machine.
- **One remote MCP server:** `https://api.investiq.live/mcp` (Streamable HTTP, OAuth 2.1 with dynamic client registration, scope `research:read`).
- **Eleven read-only tools:** `search_stocks`, `get_stock`, `get_stock_history`, `get_stock_valuation`, `screen_stocks`, `list_sectors`, `get_sector_summary`, `list_strategies`, `get_strategy_results`, `get_high_conviction_stocks`, `get_data_freshness`.
- **Data sent:** the search terms, symbols and filters Claude passes to those tools, plus your OAuth token.
- **Skills:** `research-indian-stock` and `screen-indian-stocks` (plain Markdown instructions).

## Limits

InvestIQ is research software. Valuations are model output from saved snapshots, not live quotes. It provides no personalised investment advice, no brokerage connection, no portfolio access and no trade execution. Prices and values are in INR.

## Support and policies

- Support: https://investiq.live/legal#contact
- Privacy policy: https://investiq.live/privacy
- Terms: https://investiq.live/legal#terms

Licensed under the MIT License.
