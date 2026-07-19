# 03 — MVP Definition

The MVP proves one loop: **a small retailer can issue a digital gift card or
store credit, a customer can claim it into the Spendy app, and it can be redeemed
(in part or full) at the counter.**

## In scope

- Retailer dashboard: onboard, brand a card, issue, redeem, view ledger.
- Issue gift cards two ways: at the till, and via a shareable purchase link/QR.
- Issue **store credit** (refund-as-credit) at zero cost.
- Consumer claim into the Spendy app, with graceful mobile-web fallback.
- Live balance and expiry countdown.
- **Time-based** smart reminders.
- Redemption by QR scan or short code, with **partial redemption**.

## Explicitly out of scope (for MVP)

- POS integrations (Square, Lightspeed).
- Loyalty / stamp cards.
- Promotional campaigns to card holders.
- Proximity reminders.
- Apple / Google Wallet passes.
- Multi-location support.

Naming these out loud keeps the pilot small and the build honest.

## Key design decision — the money flow

**Spendy does not hold customer funds in the MVP.** This is the single most
important architectural and regulatory choice.

Two supported payment paths:

1. **Sold at the till (primary).** The customer pays for the card on the
   retailer's own EFTPOS. Spendy staff-facing UI just issues the card object.
   Money never flows through Spendy.
2. **Sold online (secondary).** Card purchases via a shareable link settle
   **directly to the retailer** (e.g. Stripe Connect direct charges), not into a
   Spendy-controlled balance.

**Store credit** involves no purchase at all — the retailer is simply recording
value they've decided to grant, so there is no money movement.

Keeping Spendy a **ledger / software layer** rather than a stored-value holder
avoids being classed as a purchased payment facility (and the AFSL-adjacent
burden that comes with it) at the MVP stage. See
[06 — AU compliance](06-compliance-au.md) for the detail and the trigger points
that would change this.

## End-to-end flows

### A. Cafe onboards
Blackbird Cafe signs up on the dashboard, enters its ABN and payout details,
uploads its logo, and picks a warm orange for its card. Done in under five
minutes; no app to install.

### B. Customer buys a card at the counter
A regular wants to gift $50 to a friend. Staff taps "Issue gift card," enters
$50, the customer pays $50 on the cafe's EFTPOS, and staff sends the card to the
friend's number. The friend gets an SMS with a claim link.

### C. Recipient claims it
The friend taps the link. If they have the Spendy app, the card drops into their
wallet. If not, they land on a mobile-web page showing the balance and are
prompted to install Spendy to keep and use it — the acquisition moment.

### D. Partial redemption at the till
The friend visits, orders a $12 brunch, and shows their card QR. Staff scans it;
$12 comes off; the app shows **$38 remaining** and an updated expiry countdown.

### E. Store credit after a return
A customer returns an item outside the refund policy. Instead of a scribbled
note, staff issues **$30 store credit** to the customer's Spendy app in two taps.
The customer leaves with something real, and 68%-odds they come back and spend
above it.

## Pilot success metrics

Measured over a 6–8 week pilot (see [05 — Go-to-market](05-go-to-market.md)):

| Metric | Why it matters |
|--------|----------------|
| Cards issued per retailer / month | Is issuance actually easy enough to become a habit? |
| Claim rate (claimed ÷ issued) | Does the forced-download wedge convert? |
| Redemption rate vs the ~19% national expiry/loss rate | Is Spendy actually getting cards spent? |
| % of redeemers spending above card value | Validates the upsell / retention thesis |
| App installs attributable to claims | The acquisition-channel payoff |
