---
name: delta-exchange-portfolio-check
description: Read-only Delta Exchange India portfolio snapshot of balances, positions, open orders and recent fills.
api: openapi/delta-exchange-openapi.yml
operations: [getBalances, getMarginedPositions, getOrders, getUserfills, currentRateLimitQuota]
---
1. `getBalances` for wallet balances per asset.
2. `getMarginedPositions` for open positions with margin and PnL.
3. `getOrders` for currently open orders.
4. `getUserfills` for recent fills (cursor pagination with `after`/`before`, `page_size`).
5. `currentRateLimitQuota` to check remaining quota before polling further.
Use an API key with Read Data permission only.
