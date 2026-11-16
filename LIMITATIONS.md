# Limitations, stated up front

Deal Finder works within real limits. Agents using this playbook must know
them, tell the user which ones apply to their setup during intake, and
never present a workaround's output as a live check.

## Amazon blocks many agent browsers

Amazon refuses a lot of automated and agent-driven browsing: product
pages fail to load, show a bot wall, or return no prices. Whether a given
agent gets through depends on the agent, the session, and the region, so
the intake self-check records which route actually works in each setup.
Because Amazon is so often the price to beat, this is a major gap when no
route works.

Working routes:

1. **Direct**, if the agent's browser genuinely loads the product page.
   A successful direct read is a live read like any other.
2. **A browser on the user's own machine or device**, if the agent can
   drive one. A normal residential browser session usually loads Amazon
   fine, sometimes after a "continue shopping" or human-verification
   click.
3. **Price trackers**: Keepa or CamelCamelCamel give price history and
   current-price estimates. Useful for "is this a good price" and for
   watch alerts. They do not prove current stock, and a tracker price is
   not a live page read. Label it **tracker estimate**.
4. **The user checks manually** and tells the agent the price
   (**user-reported**).

Quote an Amazon price as verified only when it came from a live page or
cart read (routes 1 and 2).

## Other retailer bot walls

Some retailers block datacenter browsers, force a region, or wall off
pricing behind a login. When a page will not load, that says something
about the route, not about the product: it does not mean the item is
unavailable or the sale ended. Fall back to the user's own browser or
device when available, and say plainly which retailers could not be
checked.

## Code sites and aggregators are unreliable

Coupon aggregators list expired, invented, and region-wrong codes.
Forums and Reddit are better but still stale. That is why the playbook
tests every code in the actual cart and keeps a ledger of results: the
ledger, not the internet, becomes the source of truth over time.

## Prices and stock move

A verified price is verified at the moment it was read. Sales end, stock
sells through, and carts expire. Quotes carry the date and time they were
checked, and a price is re-verified before any purchase step.

## Marketplace condition is a judgment call

Used listings can overstate condition. The agent reports what the listing
claims, flags mismatches between photos and text, and leaves the final
call to the user. It never contacts a seller without the user's say-so.

## Program discounts vary by product

Military, teacher, and similar programs exclude specific brands, product
lines, and sometimes colors or seasonal items. Three separate things have
to line up: the user is eligible, the offer's terms cover this product,
and the discount actually applies in the cart or program flow. A
successful application does not override terms that clearly exclude the
item; when the cart and the terms disagree, the agent flags the conflict
instead of declaring a winner. Identity verification is always the user's
own step.

## Watches need a real scheduler

A watch cadence written in a config file does not make anything run. The
agent has to create and verify an actual scheduled task in its
environment (and say where alerts will be delivered), or the watch is
manual only: checked when the user asks. An agent that cannot run
unattended must not describe its watches as background monitoring.

## Scope

- Defaults are US retailers and USD. The config can change region, but
  promo sources and program discounts are US-centric until someone adds
  local ones.
- The agent prepares carts and presents deals. It does not purchase,
  redeem points, or spend gift card balances without the user's explicit
  confirmation.
