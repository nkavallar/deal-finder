# Deal Finder

A deal-hunting process for personal AI agents. It finds the best verified
price on a specific item, tests promo codes in the actual cart instead of
trusting coupon sites, and watches wishlist items until they hit a target
price. Watches run on a real scheduled task the agent creates when you
choose a watch and test-runs once on the spot; if the agent cannot run
unattended, it says so and checks when asked.

## Use it

Give your agent this repo and tell it:

> Read SKILL.md and set up Deal Finder for me.

That is the whole install. The agent will:

1. Run a short intake (a few minutes, defaults everywhere, most of it
   deferrable; if you lead with an item, the agent starts there): your
   region, any discount programs you qualify for (military, first
   responder, teacher, student, healthcare, employer programs; the agent
   highlights these in results, you do the verifier step), which
   marketplace-type sites it may search (eBay, Facebook Marketplace,
   Mercari, Poshmark, OfferUp, category-specific ones like Swappa or
   Reverb, each a separate yes or no), new vs used, and how you want
   wishlist watches to fire.
2. Check its own capabilities against your setup and tell you, in plain
   words, what will not work and what the fallback is. The known limits
   are written down in [LIMITATIONS.md](LIMITATIONS.md), Amazon being the
   big one.
3. Save your answers to a config file it reads on every run, and start
   hunting.

## How a hunt works

1. **Lock the spec.** Exact model, size, color, condition, identified from
   a link or a photo. A similar substitute is a failed search.
2. **Baseline the price** from live retailer pages. Search snippets and
   aggregator claims are leads, never evidence. Amazon, when it blocks
   the agent, is priced through Google search results and public trackers
   (CamelCamelCamel, Keepa, no accounts needed for basic lookups) and
   labeled an estimate, never a verified live price.
3. **Promo hunt.** The user's own results ledger first, then official
   promos, the discount programs from intake, forums, Reddit, Facebook
   groups, creator codes, deal communities.
4. **Test in the cart.** A code counts only when it changes the cart
   total, before vs after, including shipping-only effects. Auto-added
   shipping insurance comes out. Stacking gets checked on the combined
   total.
5. **Alternate routes.** Price matching, open-box stock, and rewards
   points converted to gift cards at per-retailer rates (the same points
   are worth different amounts at different stores, which can flip which
   deal wins).
6. **Present the best verified total.** The agent never purchases without
   the user's explicit confirmation.
7. **End at a decision point.** Buy it (cart prepared for approval),
   watch it, or pass. Watching is offered with its terms already filled
   in from the hunt: exact variant, today's price as the reference, a
   proposed target, and the places that stock it. You confirm or change
   one number.
8. **Log everything** in the ledger, so each hunt starts from evidence.

## The wishlist and watches

Hunts and watches share one personal list, the wishlist, where every
item has a status: hunting, watching, alerted, bought, or dropped. A
watch is a property of a wishlist item, not a separate system. It carries
its own target (a price ceiling, a percentage off the reference price, or
availability for unreleased products), checks on a real scheduled task,
and stays silent until the target is hit. When it fires, the agent runs a
quick hunt first, so the alert carries the current best total and the
same buy, keep watching, or drop choice, not just a raw price. A preorder
or backorder is not a release, a category-page label is not stock
evidence, and marketplace listings get their claimed condition reported
with photo mismatches flagged. The wishlist is your data: your agent
creates it locally, preferably outside the shared repo folder, and the
repo's .gitignore plus the playbook's setup rules keep it out of anything
published.

## Files

- `SKILL.md`: the agent playbook, intake through purchase review.
- `INTAKE.md`: the new-user questions, with defaults.
- `LIMITATIONS.md`: what does not work and the fallbacks, stated up front.
- `deal-finder.config.example.yaml`: the config the agent builds from
  intake.
- `templates/`: the promo-code ledger and wishlist the agent maintains.

## Example runs (real, anonymized)

From the setup this playbook was distilled from. Savings on the third
example are out-of-pocket, after a price match, a trade-in credit, and a
points-to-gift-card conversion, each shown separately in the write-up.

- **Ski kit:** a specific shell and bib in an exact size and colorway,
  tracked across US retailers; a stack of codes tested in the cart before
  purchase (one turned out to be free shipping only, two were rejected,
  all logged).
- **Unreleased product watch:** a daily watch that distinguishes actual
  retail availability from presales and backorders that look identical on
  a category page, firing only on a verified in-stock product page.
- **Big-ticket electronics:** a retailer price match plus a trade-in plus
  points converted to a gift card at that retailer's redemption rate beat
  the list price by several hundred dollars out of pocket.
