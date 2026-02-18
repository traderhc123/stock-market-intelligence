# Stock Market Intelligence

[![ClawHub](https://img.shields.io/badge/ClawHub-Install-blue)](https://clawhub.ai/traderhc123/agenthc-market-intelligence)
[![API Docs](https://img.shields.io/badge/API-Docs-green)](https://api.traderhc.com/docs)
[![Lightning](https://img.shields.io/badge/Payment-Bitcoin%20Lightning-orange)](https://api.traderhc.com/docs)

Real-time market intelligence API for AI agents. 85 intelligence modules (including 40 encoded intelligence skills) covering equities, bonds, crypto, macro, Fed, liquidity, regime detection, alpha signals, options flow, and more.

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

- **85 intelligence modules** (including 40 encoded intelligence skills) across equities, bonds, crypto, macro, and derivatives
- **Agent-optimized format** with direction, confidence, urgency, and delta tracking
- **Compact format** for 60% fewer tokens in your context window
- **Batch queries** to pull multiple modules in one request
- **Webhook events** for regime changes, VIX spikes, correlation breaks, and more
- **MCP integration** via streamable-http transport (73 tools)
- **L402 micropayments** via Bitcoin Lightning Network

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
