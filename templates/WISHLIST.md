# Wishlist

The user's personal list. One entry per item, hunted or watched. This
file is user data: it is gitignored and never published. The agent
creates it from this template during intake and deletes the example
entry. Statuses: hunting, watching, alerted, bought, dropped.

## Example item name

- Variant: exact model, size, color, condition
- Status: watching
- Added: YYYY-MM-DD, from a hunt | direct watch request
- Baseline: $0.00 at Retailer, live page, YYYY-MM-DD (the reference price
  for percent_off and any_sale targets)
- Watch target: price_ceiling $120 (product plus shipping) |
  percent_off 25 | availability | any_sale | none (hunt only)
- Where to check: retailers and marketplaces that stock it (include
  official and sold-out pages for restock watches)
- Schedule: scheduler name and task id, or "manual"; timezone; alert
  destination
- Last checked: YYYY-MM-DD HH:MM TZ
- Last observed: price, in stock yes/no
- Last alert: YYYY-MM-DD, price, retailer; lowest alerted price $0.00
  (alert again only below that, or on a return to stock)
- Hunt notes: best deal found and when, codes tested (details in the
  promo-code ledger), program discounts that apply, listings already
  seen and skipped
