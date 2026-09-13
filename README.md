# BeforeTheChart AI

BeforeTheChart AI is licensed, local decision-support software for Claude Desktop and Cursor. It combines on-demand Marketaux news sentiment with deterministic risk-based position sizing. It does not execute trades, provide personalized investment advice, or promise returns or profit.

## Tools

- `get_market_sentiment` queries Marketaux on demand for a supported market symbol and returns the provider symbol, article count, sentiment score, positive/neutral/negative counts, retrieval time, latest publication time, and source links. It never substitutes sample or fallback market data.
- `calculate_position_size` models a position from portfolio balance, risk percentage, entry price, and stop-loss price. It returns the risk budget, risk per unit, units, estimated notional value, and inferred long/short direction.

## Requirements

- Node.js 22 or newer. Use the current Node.js LTS release.
- A BeforeTheChart AI license key delivered after purchase.
- A user-owned Marketaux API token for `get_market_sentiment`. The position-size tool does not require Marketaux.

## Purchase

BeforeTheChart AI is available as a $79 one-time purchase:

[Purchase BeforeTheChart AI](https://lajuanetorrey.gumroad.com/l/beforethechart-ai)

## Claude Desktop and Cursor configuration

```json
{
  "mcpServers": {
    "BeforeTheChart": {
      "command": "npx",
      "args": ["-y", "@ltorrey/beforethechart-mcp@1.1.0"],
      "env": {
        "GUMROAD_LICENSE_KEY": "YOUR_GUMROAD_LICENSE_KEY",
        "MARKETAUX_API_TOKEN": "YOUR_MARKETAUX_API_TOKEN"
      }
    }
  }
}
```

The MCP server uses stdio and runs locally through Node.js.

## Data freshness and supported markets

Sentiment is an on-demand news query, not a real-time exchange feed. The default lookback is 72 hours. Results include timestamps, sample size, and source URLs so the user can assess freshness and evidence.

The tool is designed primarily for Marketaux-recognized stocks and cryptocurrency symbols. Other provider-recognized instruments may work when recent matching news is available. BeforeTheChart AI does not provide quotes, broker data, order routing, or trade execution.

## Privacy

The package contains no product telemetry. At startup, it sends the Gumroad product ID and license key to Gumroad for validation. A sentiment request sends the requested symbol, time filters, and the user's API token to Marketaux. Position-size inputs are calculated locally and are not sent by this package to Gumroad or Marketaux.

## Licensing, support, updates, and refunds

- One unique license key is delivered with each purchase and must not be shared or published.
- Configuration examples pin a package version so updates cannot silently change behavior. Review release notes before changing versions.
- For support, reply to the Gumroad receipt or use the creator contact on the product page. Never send a full license key or API token.
- Sales are final. Because this is digital software delivered with a unique license key, refunds are not offered except where required by applicable law or Gumroad's mandatory policies.

## Disclaimer

BeforeTheChart AI is decision-support software, not investment advice or a trading system. News sentiment can be incomplete or wrong. Position-size output does not account for slippage, gaps, liquidity, fees, taxes, broker constraints, or the user's complete financial circumstances.

Copyright 2026 Lajuane Torrey. All rights reserved.
