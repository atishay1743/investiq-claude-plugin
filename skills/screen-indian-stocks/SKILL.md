---
name: screen-indian-stocks
description: Use when the user wants to find, filter or rank Indian stocks, for example "technology stocks with 20% margin of safety", "best value picks", "high conviction ideas", "sector overview", or a named strategy such as deep value. Screens saved InvestIQ valuations.
---

# Screen Indian stocks with InvestIQ

Use the InvestIQ MCP tools. Results are saved valuation snapshots, not live data.

## Choose the tool

| Request | Tool |
| --- | --- |
| Filter by sector, margin of safety, confidence | `list_sectors` (exact sector names) then `screen_stocks` |
| Named strategy | `list_strategies`, then `get_strategy_results` with `value_investing`, `growth_value` or `deep_value` |
| Strongest model signals | `get_high_conviction_stocks` (Buy/Strong Buy with confidence above 60) |
| Sector comparison | `get_sector_summary` |

## Rules

- Use exact sector names from `list_sectors`. Margin and confidence filters are percentage points: "at least 20%" is `min_margin=20`.
- Keep `limit` small (5-10) unless the user asks for more. Maximum is 100 per call.
- Always call `get_data_freshness` and tell the user how old the scan is.
- If nothing matches, say so and suggest loosening one filter. Never fill gaps with companies from memory.
- For any shortlisted company, offer a deeper look with the `research-indian-stock` skill.
- Results are research output, not personalised advice, and InvestIQ cannot place trades.
