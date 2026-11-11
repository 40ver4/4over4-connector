---
name: track-my-orders
description: Use when a 4OVER4 customer asks about their own orders, order status, tracking, invoices, account, saved addresses or 4OVER4 coins, or wants to cancel an order (the customer cancels it on www.4over4.com). These 4over4 MCP tools need the customer to sign in with their 4OVER4.COM account.
---

# Track my 4OVER4 orders

The account tools read the signed-in customer's own data only. When the customer is not signed in, the tool returns `authed: false` and the client shows the "Sign in with 4OVER4" prompt. The customer signs in on www.4over4.com. Never ask for their password, and never ask them to paste a token.

## Which tool

| The customer asks | Call |
|---|---|
| "What are my orders?", "my delivered orders", "how much did I spend this year" | `get_my_orders` (with `status`, `search` or `insights: true`) |
| One order by its number: what is in it, where it is, the invoice | `get_order_details` with `jobId` and `view`: `details`, `tracking` or `invoice` |
| Their profile, saved addresses or QR codes | `get_my_profile` with `section` |
| Their coins balance and ledger | `get_my_coins`; ways to earn more: `loyalty_tasks` |
| Their cart on www.4over4.com | `get_cart` |

Never say an order does not exist before `get_order_details` has answered. Report the stage and dates exactly as the tool returned them.

## Cancelling an order

`get_order_cancel_link` cancels nothing. Call it, with the `jobId` when the customer names the order, and give the customer the link it returns: their orders page on www.4over4.com, where they cancel a job that can still be cancelled. Never say an order is cancelled.

## When the tools cannot help

For a damaged or wrong order, a refund or a charge question, call `search_knowledge` for the policy, then `talk_to_human` for the support contact card.
