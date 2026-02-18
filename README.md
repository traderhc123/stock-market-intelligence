# Stock Market Intelligence

[![Live Site](https://img.shields.io/badge/Live-api.traderhc.com%2Fsite-58a6ff?style=for-the-badge)](https://api.traderhc.com/site)
[![API Docs](https://img.shields.io/badge/API_Docs-green?style=for-the-badge)](https://api.traderhc.com/docs)
[![ClawHub](https://img.shields.io/badge/ClawHub-Install-blue?style=for-the-badge)](https://clawhub.ai/traderhc123/agenthc-market-intelligence)
[![Lightning](https://img.shields.io/badge/Bitcoin_Lightning-orange?style=for-the-badge)](https://api.traderhc.com/docs)

Real-time market intelligence API for AI agents. 87 intelligence modules, 40 encoded intelligence skills, and 7 named alert packages covering equities, bonds, crypto, macro, Fed, liquidity, regime detection, alpha signals, options flow, and more. Real-time alerts via webhook and Discord.

**[View Live Site](https://api.traderhc.com/site)** | **[API Documentation](https://api.traderhc.com/docs)** | **[Follow @traderhc](https://x.com/traderhc)**

## Quick Start

```bash
# Register (free, no KYC)
export AGENTHC_API_KEY=$(curl -s -X POST "https://api.traderhc.com/api/v1/agents/register" \
  -H "Content-Type: application/json" \
  -d '{"name": "MyAgent"}' | jq -r '.api_key')

# Query market intelligence
curl -s "https://api.traderhc.com/api/v1/intelligence/market_intelligence" \
  -H "X-API-Key: $AGENTHC_API_KEY" | jq '.data'
```

## Install via ClawHub

```bash
npx clawhub install agenthc-market-intelligence
```

## Modules

| Tier | Count | Includes |
|------|-------|----------|
| **Free** | 4 | Market snapshot, predictions, educational content |
| **Premium** | 23 | TA, bonds, macro, Fed, volatility, crypto, options, news, sectors |
| **Institutional** | 58 | Alpha signals, regime engine, liquidity, credit cycle, tail risk, positioning, 40 encoded intelligence skills |

## Features

- **87 intelligence modules** (including 40 encoded intelligence skills) across equities, bonds, crypto, macro, and derivatives
- **Agent-optimized format** with direction, confidence, urgency, and delta tracking
- **Compact format** for 60% fewer tokens in your context window
- **Batch queries** to pull multiple modules in one request
- **Webhook events** for regime changes, VIX spikes, correlation breaks, and more
- **MCP integration** via streamable-http transport (73 tools)
- **7 named alert packages** — enriched, real-time alerts via webhook and Discord
- **L402 micropayments** via Bitcoin Lightning Network

## Alert Packages

Pre-built intelligence products that deliver enriched, real-time alerts when market conditions change. Each alert includes signal data, regime context, positioning implications, and affected tickers.

| Package | Tier | Price | Triggers |
|---------|------|-------|----------|
| **Regime Shift** | Premium | ~$25/mo | Market regime changes, risk-on/off transitions |
| **Tail Risk** | Institutional | ~$100/mo | Elevated/severe tail risk, crisis early warnings |
| **Volatility** | Premium | ~$25/mo | VIX spikes, vol regime changes |
| **Credit Cycle** | Premium | ~$25/mo | Spread blowouts, cycle shifts, stress spikes |
| **Liquidity** | Institutional | ~$100/mo | Fed liquidity regime changes |
| **Cross-Market** | Premium | ~$25/mo | Correlation breaks, alpha signal flips |
| **Smart Money** | Institutional | ~$100/mo | Smart/dumb money divergence |

```bash
# List all packages
curl -s "https://api.traderhc.com/api/v1/alert-packages" | jq '.packages'

# Subscribe (webhook delivery)
curl -s -X POST "https://api.traderhc.com/api/v1/alert-packages/regime_shift/subscribe" \
  -H "X-API-Key: $AGENTHC_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"callback_url": "https://your-agent.com/webhook"}'

# Subscribe (Discord delivery)
curl -s -X POST "https://api.traderhc.com/api/v1/alert-packages/tail_risk/subscribe" \
  -H "X-API-Key: $AGENTHC_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"discord_webhook_url": "https://discord.com/api/webhooks/..."}'
```

Live alerts also stream to **#agenthc-market-alerts** on Discord.

## Pricing

| Tier | Rate | Cost |
|------|------|------|
| Free | 10/min, 100/day | $0 |
| Premium | 60/min, 5,000/day | ~$50/mo (50K sats) |
| Institutional | 120/min, 50,000/day | ~$500/mo (500K sats) |

## API Docs

Full documentation at [api.traderhc.com/docs](https://api.traderhc.com/docs)

## Disclaimer

All data and analysis is for educational and informational purposes only. Not financial advice. Not a registered investment advisor. Always do your own research.
