# 02 — Feature Vision

Features are tagged by release stage:

- **[MVP]** — in the first pilot build.
- **[v1.x]** — fast-follow after the pilot proves the core loop.
- **[later]** — on the roadmap, not near-term.

Loyalty (stamp cards) is deliberately a fast-follow, not MVP — the MVP is
gift-cards-first.

---

## Retailer-facing (web dashboard, mobile-friendly)

### Onboarding & branding
- **[MVP]** Self-serve sign-up: business name, contact, ABN, payout details.
- **[MVP]** Card branding: upload a logo, pick a card colour. The card the
  customer sees in the app carries the retailer's identity.
- **[later]** Multi-location support for small chains.

### Issuing gift cards
- **[MVP]** **In-store issuance** — staff creates a card at the counter for any
  value; the customer pays on the retailer's own EFTPOS; the card is delivered
  to the customer by SMS/email link or on-screen QR.
- **[MVP]** **Online / shareable purchase link** — a link or QR the retailer can
  post to socials or sit on the counter, so anyone can buy a card for themselves
  or as a gift.
- **[MVP]** **Store credit** — issue refund-as-credit on the same rails at zero
  cost. This is the "better than no refund" goodwill moment and the same object
  as a gift card under the hood.

### Redemption
- **[MVP]** Staff scans the customer's QR from the Spendy app, or enters a short
  code, to redeem.
- **[MVP]** **Partial redemption** with a live remaining balance — critical for
  cafes where a card covers several visits.

### Reporting & ledger
- **[MVP]** Outstanding liability at a glance (total unredeemed value issued).
- **[MVP]** Issued vs redeemed totals, per-card history, expiry dates.
- **[MVP]** CSV export for the retailer's bookkeeping.
- **[v1.x]** Redemption-rate and average-uplift dashboards (how much customers
  spend above card value).

### Customer insight
- **[v1.x]** Who holds unspent value (from opt-in customer profiles).
- **[v1.x]** Repeat-visit and retention metrics tied to issued cards.

### Growth & engagement
- **[v1.x]** Opt-in promotional pushes to the retailer's card holders (customer
  opts in; retailer can nudge "you've got $23 left").
- **[v1.x]** **Loyalty / digital stamp cards** — "buy 9, get the 10th free"
  coffee cards, the daily-use hook for cafes.
- **[later]** POS integrations (Square, Lightspeed) so issuance/redemption happen
  inside the existing till flow.
- **[later]** Apple / Google Wallet passes for cards.

---

## Consumer-facing (inside the existing Spendy app)

- **[MVP]** **Claim flow** — a card arrives via link/QR and is claimed into the
  app. This is the forced-download wedge. It must also degrade gracefully to
  mobile web so a card can be gifted to someone who isn't a Spendy user yet.
- **[MVP]** **Live balance** and **expiry countdown** per card.
- **[MVP]** **Time-based smart reminders** — "You have $23 left at Blackbird
  Cafe, expiring in 30 days."
- **[MVP]** **Gifting** — buy a card for someone else, delivered by SMS/email
  with a claim link.
- **[v1.x]** Consolidated wallet across all retailers, physical and digital
  cards, store credit, and coupons in one place (the core consumer promise —
  consolidated beats dispersed, à la Stocard).
- **[later]** **Proximity reminders** — nudge when the customer is near a
  retailer they hold a balance with.

---

## What ties the two sides together

The retailer never touches an app build; the consumer never juggles 100
single-store apps. The retailer dashboard issues value, the Spendy app holds and
reminds. Every issued card is simultaneously a retention tool for the retailer
and a new (or returning) user for Spendy.
