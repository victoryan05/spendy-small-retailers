# 06 — Australian Compliance Notes

Not legal advice — a planning checklist of the AU rules that shape the product.
Confirm specifics with a lawyer before launch.

## Gift card expiry law (Australian Consumer Law)

Since **1 November 2019**, nationally:

- Gift cards must have a **minimum 3-year expiry** from the date of purchase.
- The **expiry date must be displayed** (or state that there is no expiry).
- **No post-supply fees** — businesses can't charge activation, account-keeping,
  or balance fees after purchase (some payment-related exceptions exist).

**Product implications:**

- Default issued cards to **3-year or no expiry**, and surface compliance in the
  dashboard so retailers don't have to think about it.
- Turn it into a **selling point**: "Spendy cards are compliant by default."
- Store credit issued as goodwill isn't a purchased gift card in the same sense,
  but defaulting to generous/no expiry keeps it customer-friendly and avoids
  edge-case disputes.

## Breakage and liability accounting

- Unredeemed value is a **liability** on the retailer's books until spent or
  expired, then recognised as breakage revenue.
- **No-expiry cards** (the Mecca example) never age off — the liability is
  effectively permanent, which is exactly the pain Spendy's reminders resolve by
  driving redemption.
- The retailer ledger in [02 — Features](02-features.md) should surface
  outstanding liability clearly so retailers can see and manage it.

## Why the money-flow decision keeps regulatory scope small

The MVP choice that **Spendy never holds customer funds** (see
[03 — MVP](03-mvp.md)) is what keeps Spendy out of stored-value / payments
licensing at this stage:

- Cards are paid on the retailer's own EFTPOS, or settle **directly to the
  retailer** via a payment integration.
- Spendy is a **ledger / software layer**, not a holder of value.

**Trigger points that would change this** (and require licensing/legal review
before doing):

- Holding customer balances in a Spendy-controlled account.
- Issuing value redeemable across **multiple, unrelated retailers** (moves toward
  a **purchased payment facility** and potential AFSL territory).
- Facilitating cash-out or transfers between users.

Design the MVP to stay clear of all three.

## Unclaimed money

- Several states (e.g. NSW) have **unclaimed money** regimes. Whether expired
  gift card balances fall in scope varies and interacts with the ACL expiry
  rules — flag for legal review, especially for any no-expiry product.

## Privacy

- The opt-in **customer profiles** and insight features collect personal
  information, so the **Privacy Act / Australian Privacy Principles** apply:
  clear consent for the opt-in, purpose limitation, secure storage, and a way for
  customers to access or delete their data.
- Keep customer-insight data **opt-in** (as the pitch already frames it) rather
  than default-on.
