---
name: delta-exchange-place-and-manage-order
description: Look up a Delta Exchange India product, place a limit order, check it and cancel it if still open.
api: openapi/delta-exchange-openapi.yml
operations: [getProduct, getTicker, placeOrder, getOrderById, cancelOrder]
---
1. `getProduct` with the symbol (e.g. BTCUSD) to read the product id, contract size and tick size.
2. `getTicker` for the current mark/last price.
3. `placeOrder` (signed: api-key, signature, timestamp headers; signatures older than 5 seconds fail with SignatureExpired). Set a `client_order_id` so the order can be found again. There is no documented idempotency key: do not blindly retry a timed-out placeOrder; check first.
4. `getOrderById` to confirm state.
5. `cancelOrder` to withdraw it while open. Filled trades cannot be reversed.
Rate limits: weighted 20000-unit quota per 5 minutes plus 500 operations/second per product; on 429 wait for `X-RATE-LIMIT-RESET` ms. Use the Demo testnet (https://cdn-ind.testnet.deltaex.org) with Demo keys to rehearse.
