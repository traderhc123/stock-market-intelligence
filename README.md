# Stock Market Intelligence

[![Live Site](https://img.shields.io/badge/Live-api.traderhc.com%2Fsite-58a6ff?style=for-the-badge)](https://api.traderhc.com/site)
[![API Docs](https://img.shields.io/badge/API_Docs-green?style=for-the-badge)](https://api.traderhc.com/docs)
[![Lightning](https://img.shields.io/badge/Bitcoin_Lightning-orange?style=for-the-badge)](https://api.traderhc.com/docs)

Market data API for AI agents and developers. Covers equities, fixed income, crypto, and macro. Real-time alerts via webhook and Discord. Bitcoin Lightning micropayments.

**[View Live Site](https://api.traderhc.com/site)** | **[API Documentation](https://api.traderhc.com/docs)** | **[Follow @traderhc](https://x.com/traderhc)**

## Quick Start

```bash
# Register (free, no KYC)
export API_KEY=$(curl -s -X POST "https://api.traderhc.com/api/v1/register" \
  -H "Content-Type: application/json" \
  -d '{"name": "MyAgent"}' | jq -r '.api_key')

# Query market data
curl -s "https://api.traderhc.com/api/v1/data/overview" \
  -H "X-API-Key: $API_KEY" | jq '.data'
```

## Features

- Market data across equities, fixed income, crypto, and macro
- Agent-optimized format with direction, confidence, and urgency signals
- Compact format for reduced token usage in LLM context windows
- Batch queries to pull multiple datasets in one request
- Webhook alerts for key market events
- L402 micropayments via Bitcoin Lightning Network

## Tiers

| Tier | Rate | Cost |
|------|------|------|
| Free | 5/min, 1/day on the intelligence endpoints | 0 sats |
| Premium | 60/min, 5,000/day | 50,000 sats (~$50) one-off for 30 days; does not renew |
| Institutional | 120/min, 50,000/day | 500,000 sats (~$500) one-off for 30 days; does not renew |

Requests after the free daily one cost 50 sats each from a prepaid balance (Premium tier or above). Dollar figures are approximate; you are charged the sats amount. All sales are final. Authoritative prices: `GET /api/v1/pricing`.

Payment via Bitcoin Lightning Network. Instant settlement, no KYC.

## API Docs

Full documentation and endpoint catalog at [api.traderhc.com/docs](https://api.traderhc.com/docs).

## Disclaimer

All data and analysis is for educational and informational purposes only. Not financial advice. Not a registered investment advisor. Always do your own research.
