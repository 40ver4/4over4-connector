---
name: find-and-price-print
description: Use when someone wants to find a print product at 4OVER4 (business cards, flyers, postcards, signs, labels, stickers, invitations and more), compare products, get a live price for a quantity, see price breaks, or ask when an order would arrive. Uses the 4over4 MCP tools.
---

# Find and price print at 4OVER4

4OVER4.COM is a US online print shop that prints in its own plant in Queens, NY. The `4over4` MCP server in this plugin gives live product, price and delivery data. Every price, size, paper, turnaround and policy you tell the customer comes from a tool result in this conversation. When a tool did not return it, say you cannot confirm it and offer to check with the tools.

## 1. Find the product

| The customer says | Call |
|---|---|
| A product or a kind of product ("foil business cards", "gym flyers") | `show_products`. Put a product type with an angle in `angle` and `productType`, not in `query`. |
| "What do you have?" | `list_categories` |
| A goal with no product ("how do I promote my bakery") | `recommend` |
| Several products for one goal or a campaign | `marketing_kit` |
| "Something like this one" | `find_similar_products` |
| "What goes with this one?" | `find_matching_print_products` |
| "Which is better, A or B?" | `compare_products` with 2 to 4 slugs |

Show one result at a time with a one-line reason. Ask one short question when the product is not clear yet.

## 2. Price it

- `configure_product` gives the live total and the price per piece for one product, quantity, size, paper, finish and turnaround. Call it again when the customer changes any option.
- A quantity snaps to the nearest real tier. When the result says so, tell the customer the quantity that was priced.
- `price_breaks` gives the table of every quantity tier for one product, for "how much cheaper if I order more".
- Print math: `calculate_print_resolution` (pixels and DPI), `calculate_print_bleed` (bleed and safe area), `convert_paper_weight` (paper weights), `get_print_file_setup` (a file's setup).
- `daily_deals` shows today's deal and its code.

## 3. Delivery dates

`delivery_by_zip` with `quick: true` gives an in-hands estimate for a product. With a `slug` and a `zip` it gives the live carrier options. Turnaround is an estimate, never a guarantee: say "estimated" beside every date.

## 4. Questions about policy, files or help

`search_knowledge` answers support, policy and how-to questions from the 4OVER4 help center. Pass your own search words for what the customer wants, with the product name. When the customer asks for a person, or the tools cannot answer, call `talk_to_human` for the support contact card.

## 5. Next step

End with the www.4over4.com link from the tool result. To build an order, use the `order-on-4over4` skill.
