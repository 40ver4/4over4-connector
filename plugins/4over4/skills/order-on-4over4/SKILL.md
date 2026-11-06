---
name: order-on-4over4
description: Use when someone has picked a 4OVER4 print product and wants to order it, put it in a cart or check out. It builds the configured cart with the 4over4 MCP tools and hands the customer a link to www.4over4.com, where they upload artwork, choose shipping and pay.
---

# Order on 4OVER4

**No payment happens in the chat.** The 4over4 tools build the order and return a link. The customer opens the link, and on www.4over4.com they upload their artwork, choose shipping and pay. Never ask for a card number or any payment detail.

## 1. Confirm the configuration

Before you build a cart, confirm with the customer the product, quantity, size, paper, finish and turnaround. Price it with `configure_product` if the conversation has no live price for that exact configuration yet.

## 2. Build the cart

| Step | Call |
|---|---|
| Find the variant id | `search_catalog`, `lookup_catalog` or `get_product` (with `selected` to narrow the options) |
| Make a cart | `create_cart` with the variants and quantities. The result has live estimated totals and a `continue_url`. |
| Change it | `update_cart` replaces the line items |
| Make a checkout | `create_checkout` from the line items or from the cart id |
| Finish | `complete_checkout` places nothing and charges nothing. It answers `requires_escalation` with the `continue_url`. |
| Stop | `cancel_cart` or `cancel_checkout` when the customer changes their mind |

## 3. Hand off

Give the customer the `continue_url` from the tool result, as it came. Never build or edit a link yourself. Tell them in one line what happens there: the lines go into their own 4OVER4 cart, and on www.4over4.com they sign in, upload artwork, choose shipping and pay.

Totals in the chat are estimates. The final price, tax and shipping show on www.4over4.com before the customer pays.

## Notes

- A product the cart tools cannot take (for example a custom job with a different name on each piece) is a custom quote: call `talk_to_human`.
- After the order is placed, the `track-my-orders` skill reads its status.
