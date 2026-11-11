---
name: order-on-4over4
description: Use when someone has priced a 4OVER4 print product and wants to order it or check out. It takes the priced setup to the Checkout on 4OVER4 button or the link from the 4over4 MCP tools, which opens www.4over4.com, where they upload artwork, choose shipping and pay.
---

# Order on 4OVER4

**No payment happens in the chat.** The 4over4 tools price the setup and return a link. On www.4over4.com the customer uploads artwork, chooses shipping and pays. Never ask for a card number or any payment detail.

## 1. Confirm the setup

Confirm with the customer the product, quantity, size, paper, finish and turnaround. Price it with `configure_product` if the conversation has no live price for that exact setup yet.

## 2. Hand off

The price card shows a Checkout on 4OVER4 button. The customer presses it. In a client that shows no card, give the order link from the `configure_product` result, as it came. Never build or edit a link yourself.

The customer's own cart on www.4over4.com can be read with `get_cart` after sign-in. Items are added on www.4over4.com product pages.

Totals in the chat are estimates. The final price, tax and shipping show on www.4over4.com before the customer pays.

## Notes

- A job the setup cannot express (for example a different name on each piece) is a custom quote: call `talk_to_human`.
- After the order is placed, the `track-my-orders` skill reads its status.
