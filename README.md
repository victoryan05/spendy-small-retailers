# Spendy for Small Retailers

Product plan for Spendy's B2B offering aimed at **small retailers — cafes, coffee
shops, and restaurants**. This is the workspace for planning how Spendy helps
these businesses issue **digital gift cards** (with loyalty as a fast-follow),
and how that doubles as the acquisition wedge that gives consumers a reason to
download the Spendy app.

## The idea in one paragraph

Small retailers have no good way to issue digital gift cards or store credit
today. They hand out paper vouchers that get lost, scribble store credit on the
back of a receipt, or offer nothing at all. Spendy gives them a simple dashboard
to issue and redeem digital gift cards and store credit — no app for them to
build, no POS to replace. Every card they issue lands in the recipient's Spendy
app, which is how Spendy grows its consumer base: each issued card is a funded
reason for a new person to download and return.

## Why this matters

- **~$1.4B** of gift cards sit unredeemed across Australia (Finder).
- **1 in 3** Australians hold at least one unused gift card; almost **1 in 5**
  have had a card expire before use (Finder).
- The Australian gift card market was valued at **AUD 11.94B in 2025**, with
  **60%+** of sales already digital (EMR 2025; ARA 2023).

Small retailers are the underserved edge of this market and the cheapest place
for Spendy to start acquiring both sides at once.

## The flywheel

```
Retailer issues a card via Spendy
        │
        ▼
Recipient claims it in the Spendy app  ◄── forced-download wedge
        │
        ▼
Spendy gains a consumer user with money to spend
        │
        ▼
User returns, redeems, and spends above card value
        │
        ▼
Retailer sees retention → issues more cards
```

## Documents

| # | Doc | What's in it |
|---|-----|--------------|
| 01 | [Opportunity](docs/01-opportunity.md) | The small-retailer angle on the market, the retention-vs-breakage argument, the flywheel |
| 02 | [Features](docs/02-features.md) | Full feature vision, retailer and consumer side, tagged MVP / v1.x / later |
| 03 | [MVP](docs/03-mvp.md) | Tight MVP scope, the money-flow decision, end-to-end flows, pilot metrics |
| 04 | [Business model](docs/04-business-model.md) | How Spendy charges small retailers; the recommendation |
| 05 | [Go-to-market](docs/05-go-to-market.md) | University-precinct launch, referral engine, pilot plan |
| 06 | [AU compliance](docs/06-compliance-au.md) | Gift card law, expiry rules, breakage, the regulatory reason for the money-flow choice |

## Status

Planning stage. The consumer app theme lives in
[`victoryan05/smart-spend-buddy`](https://github.com/victoryan05/smart-spend-buddy);
this repo holds the small-retailer product plan.
