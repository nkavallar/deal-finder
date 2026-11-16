# Promo code ledger

Every code tested, with its result. The agent checks this before hunting
for new codes and appends a row after every test. A code counts as working
only when it changed the cart total (before vs after, same item, quantity,
shipping method, and destination). The ledger records what worked once;
retest before relying on an old result. Delete the example row when this
file is created during intake.

| Date and time (with timezone) | Retailer | Code | Source | Claimed | Before total | After total | Result | Item or category | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2026-01-01 10:00 MST | Example Outfitters | EXAMPLE20 | Aggregator | 20% off | $100.00 | $100.00 | Rejected | Sitewide test | Expired |

## Purchases

Completed purchases, recorded when they happen.

| Date | Item | Price paid | Retailer | Warranty | Notes |
| --- | --- | --- | --- | --- | --- |
