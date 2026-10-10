---
name: agenthc-market-intelligence
description: Market data API for AI agents. Equities, fixed income, crypto, and macro. Bitcoin Lightning micropayments.
homepage: https://api.traderhc.com/docs
metadata:
  clawdbot:
    emoji: "📊"
    requires:
      env: ["AGENTHC_API_KEY"]
      bins: ["curl", "jq", "python3"]
    primaryEnv: "AGENTHC_API_KEY"
license: UNLICENSED
---

# Stock Market Intelligence

Market data API for AI agents and developers. Covers equities, fixed income, crypto, and macro. Real-time alerts via webhook and Discord. Bitcoin Lightning micropayments. Built by @traderhc.

## Setup

### For AI Agents

```bash
export AGENTHC_API_KEY=$(curl -s -X POST "https://api.traderhc.com/api/v1/register" \
  -H "Content-Type: application/json" \
  -d '{"name": "MyAgent"}' | jq -r '.api_key')
```

Free, no KYC, no credit card. Query any free endpoint:

```bash
curl -s "https://api.traderhc.com/api/v1/data/overview" \
  -H "X-API-Key: $AGENTHC_API_KEY" | jq '.data'
```

### Interactive Setup

```bash
bash scripts/setup.sh
```

### Non-Interactive (CI/scripts)

```bash
export AGENTHC_API_KEY=$(bash scripts/setup.sh --auto)
```

## What's Available

| Tier | Coverage | Cost |
|------|----------|------|
| **Free** | Market overview, educational content | $0 |
| **Premium** | Equities, fixed income, macro, crypto, volatility | 50,000 sats (~$50) for 30 days, one-off |
| **Institutional** | Full platform access with advanced analytics | 500,000 sats (~$500) for 30 days, one-off |

See [api.traderhc.com/docs](https://api.traderhc.com/docs) for the full endpoint catalog.

## Agent-Optimized Format

Use `format=agent` for actionable signals:

```bash
curl -s "https://api.traderhc.com/api/v1/data/overview?format=agent" \
  -H "X-API-Key: $AGENTHC_API_KEY" | jq '.signals'
```

## Compact Format

Use `format=compact` for reduced token usage:

```bash
curl -s "https://api.traderhc.com/api/v1/data/overview?format=compact" \
  -H "X-API-Key: $AGENTHC_API_KEY" | jq '.'
```

## Batch Queries (Premium+)

Query multiple endpoints in one request:

```bash
curl -s -X POST "https://api.traderhc.com/api/v1/data/batch" \
  -H "X-API-Key: $AGENTHC_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"endpoints": ["overview", "fixed_income", "macro"]}' | jq '.'
```

## Alerts

Subscribe to real-time market alerts via webhook or Discord:

```bash
# List available alert types
curl -s "https://api.traderhc.com/api/v1/alerts" \
  -H "X-API-Key: $AGENTHC_API_KEY" | jq '.alerts'

# Subscribe via webhook
curl -s -X POST "https://api.traderhc.com/api/v1/alerts/subscribe" \
  -H "X-API-Key: $AGENTHC_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"type": "market_events", "callback_url": "https://your-agent.com/webhook"}' | jq '.'
```

## Lightning Payment (L402)

For per-request payment without registration:

1. Request a premium endpoint without auth
2. Receive 402 response with Lightning invoice
3. Pay the invoice (any Lightning wallet)
4. Re-request with `Authorization: L402 <macaroon>:<preimage>`

## Pricing

| Tier | Rate | Cost |
|------|------|------|
| Free | 5/min, 1/day on the intelligence endpoints | 0 sats |
| Premium | 60/min, 5,000/day | 50,000 sats (~$50) one-off for 30 days; does not renew |
| Institutional | 120/min, 50,000/day | 500,000 sats (~$500) one-off for 30 days; does not renew |

Requests after the free daily one cost 50 sats each from a prepaid balance (Premium tier or above). Dollar figures are approximate; you are charged the sats amount. All sales are final. Authoritative prices: `GET /api/v1/pricing`.

Payment via Bitcoin Lightning Network. Instant settlement, no KYC.

## Disclaimer

All data and analysis is for educational and informational purposes only. Not financial advice. Not a registered investment advisor. Always do your own research.
