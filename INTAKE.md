# Intake

Run this once, when a new user sets up Deal Finder. Ask in one pass,
grouped by section, in plain language. Every section has a sensible
default; "just use the defaults" is always an acceptable answer. The goal
is a few minutes, not a form.

Short on time? The minimum viable setup is section 1 plus the defaults
for everything else. Sections 2 to 8 can be deferred and answered later,
per hunt, when they actually matter. Say so, show the default summary,
and move on.

Write the answers into `deal-finder.config.yaml`. Anything left blank
keeps the default shown here.

## 1. Basics

- Country and currency for prices? (Default: US, USD.)
- ZIP or postal code, for shipping and tax estimates? (Optional.)

## 2. Discount programs

"Do you qualify for any of these? They change which deals are best, so the
agent checks them first."

- Military or veteran
- First responder (police, fire, EMT, dispatch)
- Teacher or school staff
- Student
- Healthcare worker
- Government employee
- An employer's discount program or corporate perks portal
- Warehouse clubs: Costco, Sam's Club, BJ's
- Verified through ID.me, VerifyPass, UNiDAYs, or similar? (Which ones?)

Default: none. The agent still checks public promos for everyone.

## 3. Marketplaces and condition

- Search used marketplaces too? eBay, Facebook Marketplace, Craigslist,
  Mercari, Poshmark. (Default: eBay on, the rest off until asked.)
- New items only, or is used OK? For which categories is used acceptable,
  and which are always new-only? (Default: new only. Common pattern: used
  OK for tools, parts, and gear; new only for clothing, footwear, and
  anything worn against skin.)

## 4. Retailers

- Favorite retailers the agent should prefer when prices are close?
- Any retailers to never use?

## 5. Promo tactics

- OK to sign up for a retailer's newsletter to get a signup discount code?
  (Default: ask each time.)
- If yes: use a throwaway inbox the agent creates and monitors, or your
  own email? (Default: throwaway.)
- Cashback portals (Rakuten and similar)? (Default: off.)

## 6. Rewards and gift cards

- Do you hold transferable points (Amex Membership Rewards, Chase Ultimate
  Rewards, Citi, Capital One)? (Default: none recorded.)
- OK for the agent to compare converting points to retailer gift cards
  when it changes which deal wins? Rates differ per retailer, sometimes a
  lot. (Default: yes, compare; never redeem without asking.)

## 7. Buying rules

- The agent never buys without your explicit confirmation. (Not optional.)
- Should it prepare the cart up to the final review step so you can
  one-tap approve? (Default: yes.)
- Price matching: OK to pursue a price match at a preferred retailer
  instead of the raw lowest price? (Default: yes.)

## 8. Wishlist watches

- Default watch target when you don't specify one: a percentage off the
  price recorded when the watch starts, a fixed price ceiling (product
  price plus shipping where known), or any verified drop below the
  starting price? (Default: 25% off the starting price.)
- Check cadence? (Default: daily.) A cadence only works if the agent sets
  up a real scheduled task; if it cannot run unattended, watches are
  checked when you ask, and the agent will say so.
- Where should a fired watch reach you: this chat, email, somewhere else?
  (Default: this chat.)

## 9. Capability self-check (the agent fills this in, not the user)

Before finishing intake, verify and record in the config, each one
separately (being able to do one says nothing about the others):

- Browse live retailer product pages? Which major ones fail?
- Work a cart: add items, apply codes, read before and after totals?
  If not, discounts will be reported as untested and code testing is
  handed to the user.
- Persist files and run on a schedule (needed for watches and the
  ledger)? Record the scheduler you will use, or mark watches manual.
- Access each marketplace the user enabled? Natively, via the browser,
  or not at all?
- Amazon: can you read Amazon product pages directly? Many agent
  browsers cannot (see LIMITATIONS.md). Record the working route:
  direct, price tracker (Keepa or CamelCamelCamel), the user's own
  device browser, or manual check by the user.
- Access the user's discount program accounts, or will the user apply
  those discounts themselves at checkout? (The agent never submits
  identity documents or verification on the user's behalf.)
- Create and monitor a throwaway inbox, if the user opted into
  newsletter codes that way? This is provider-dependent; if you cannot,
  say so and fall back to asking each time.
- Send the user notifications when a watch fires?

Tell the user, once and in plain words, any enabled route that does not
actually work in their setup, and what the fallback is. Then write the
config and start.
