---
name: research-indian-stock
description: Use when the user asks to research, analyse, value or compare a specific Indian listed company (NSE/BSE), for example "is Infosys undervalued", "show TCS fundamentals", or "what is the intrinsic value of HDFC Bank". Resolves the symbol, pulls the saved InvestIQ valuation, and reports it with data age.
---

# Research an Indian stock with InvestIQ

Use the InvestIQ MCP tools. They are read-only and return saved snapshots, not live quotes.

## Steps

1. **Resolve the symbol.** Call `search_stocks` with the company name. Use the exchange-qualified symbol it returns (for example `INFY.NS`). Never guess a symbol.
2. **Fundamentals.** Call `get_stock` for price, ratios and analyst sentiment.
3. **Valuation.** Call `get_stock_valuation`. Report the composite intrinsic value, margin of safety, confidence, valuation tag, and each underlying model (DCF, DDM, RIM, EPV, Relative) with the assumptions that matter. If `composite` is null, say no saved valuation exists; do not estimate one.
4. **Data age.** Call `get_data_freshness`. State the valuation `computed_at`, the stock `updated_at` and the last completed scan. `retrieved_at` is only the response time, not the age of the market data.
5. **History (optional).** Call `get_stock_history` when the user asks about price trend. `observations` counts stored trading records, not calendar days.

## Reporting rules

- Prices and intrinsic values are in INR. Margin of safety and confidence are percentage points (`30` means 30%).
- Where models disagree widely, say so; low confidence means weak model agreement or data quality.
- Describe tags such as "Buy" as model output, not advice. InvestIQ gives research only: no personalised investment advice, no brokerage access, no trade execution. If asked to buy or sell, explain that it cannot.
- Never invent numbers for missing fields. Say they are unavailable.
