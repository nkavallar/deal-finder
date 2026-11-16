# Wishlist watches

One entry per watched item. The agent checks on the cadence in
`deal-finder.config.yaml` (via the scheduled task recorded during intake)
and stays silent until a target is hit. Delete the example when this file
is created during intake.

## Example item name

- Variant: exact model, size, color
- Target: price_ceiling $120 (product plus shipping) | percent_off 25 |
  availability | any_sale
- Reference price: $0.00 at Retailer, live page, YYYY-MM-DD (required for
  percent_off and any_sale targets)
- Where: retailers and marketplaces to check
- Schedule: scheduler name and task id, or "manual"
- Status: watching | alerted | paused | fulfilled
- Last checked: YYYY-MM-DD HH:MM TZ
- Last alert: YYYY-MM-DD, price, retailer (alert again only on a new low
  or a return to stock)
- Notes: anything that changes the hunt (price-match candidates, program
  discounts that apply, listings already seen and skipped)
