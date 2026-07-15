# Handoff block — output contract

Use these exact headers and order. Keep prose tight. State unknowns as unknowns.

```
# 🧭 Design handoff — <Section name>

**Date:** <YYYY-MM-DD>
**Owners:** <Figma current user>, <collaborators named by the designer>
**Figma:** <file / node link or node id>

## 1. Brief
<What this section is and what we aimed to achieve as designers. Grounded in the
confirmed job-to-be-done. 1–3 short paragraphs, no filler.>

## 2. Flow structure
<What the reader sees and where it lives in the file. List frames/screens in order,
key components, states, and how they connect. Use real frame/node names.>
- <Frame name> — <what it is, what's on it>
- <Frame name> — <…>
- States: <empty / loading / error / success, where they appear>

## 3. Looker metrics
Five data points this design should move (Uphold data via Looker).

| Before | After | Design impact & tracking |
|--------|-------|--------------------------|
| <live value> | <target/hypothesis, confirmed> | <how the design moves it + which Look/Explore, dimension, cadence to track it> |
```

---

## Filled example (illustrative — not real numbers)

```
# 🧭 Design handoff — Markets revamp · discovery feed

**Date:** 2026-07-15
**Owners:** M. Hennemann (Figma), plus J. Silva (research)
**Figma:** business-experience-designer / node 1245:8890

## 1. Brief
The Markets landing was a flat, undifferentiated list. This revamp reorganises it
into intent-based zones — a personalised "Minted for you" strip, a best-rates rail,
a market-pulse block, theme categories, and an equities spotlight — so a returning
user reaches a relevant asset in fewer taps. Goal: lift discovery of earn/staking
products without burying the core "buy top crypto" path.

## 2. Flow structure
- Sticky nav — title, search, filter pills (Assets / Stocks & ETFs / Stablecoins).
- Zone 1 "Minted for you" — personalised card, shown only when isPersonalized.
- Zone 2 "Best rates" — horizontal rail of rate cards → Start earning CTA.
- Zone 3 "Market pulse" — top performer card, top-crypto list, two-col Most bought /
  Recently added.
- Zone 4 "Crypto categories" — themed horizontal cards.
- Zone 5 "Equities spotlight" — stock/ETF cards with signal line.
- Sort & filter bottom sheet (showBottomSheet state).
- States: guest (no Zone 1), bullish/bearish data variants.

## 3. Looker metrics
| Before | After | Design impact & tracking |
|--------|-------|--------------------------|
| 3.1% earn-product CTR | 6% (target) | Best-rates rail surfaces APYs above the fold; track rate-card tap-through in the Markets Explore, weekly. |
| 4.2 taps to first asset view | ≤2 taps | Intent zones shorten the path; track median taps-to-asset via funnel dimension, weekly. |
| 12% search usage | 20% | Prominent search bar; track search-open rate, weekly. |
| 1.8% staking start rate | 3% | Flexibility labels reduce friction; track Start-earning conversions, biweekly. |
| 22% guest→signup on Markets | 28% | Personalised teaser drives signup; track guest CTA conversion, weekly. |
```
