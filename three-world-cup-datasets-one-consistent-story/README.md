---
title: "Three World Cup Datasets, One Consistent Story: Carbon Up 92%, Tickets Up 6.8×, Prize Money at $655M"
description: "We built and published three fully documented, CSV-downloadable datasets covering the 2026 World Cup. Here is what we found — and how we handled the data quality problems that make most World Cup numbers unreliable."
date: 2026-06-15
authors: [Anuar Ustayev, Yoana Popova]
---

![[world-cup-1.png]]

[The 2026 FIFA World Cup](https://www.fifa.com/en/tournaments/mens/worldcup/canadamexicousa2026) is the most commercially and environmentally consequential tournament ever staged. It is also one of the most data-polluted: carbon figures that compare incompatible accounting scopes, ticket prices that mix face value with resale, prize money totals that shift definition between editions.

We spent the past month building three datasets that treat these problems explicitly rather than silently. The methodology notes are in the data. The exclusions are flagged. The scope differences are labelled.

Here is what the numbers show when handled carefully.

## Dataset 1: World Cup Carbon Footprint

![[airplane.png]]

→ [worldcup-carbon-footprint on DataHub](https://datahub.io/football/worldcup-carbon-footprint)

The 2026 tournament is projected at 9.0 million tonnes of CO₂ equivalent — roughly the annual emissions of 2 million cars.

The number that matters more is the comparison: against a recalculated 2010–2022 average of 4.71 Mt on a consistent accounting basis, 2026 represents a +92% increase.

### The data quality problem this dataset solves

FIFA's published historical figures — South Africa 2.75 Mt, Brazil 2.27 Mt, Russia 2.16 Mt, Qatar 3.63 Mt — use a narrower accounting boundary that systematically excludes or undercounts aviation. Comparing 2026's full-scope projection directly to those figures produces a misleading comparison. We recalculated historical figures on a consistent fuller scope before making any cross-edition comparisons.

The structural driver is unambiguous: 86% of projected 2026 emissions — 7.72 million tonnes — comes from air travel. A 48-team tournament spread across three nations on a continent-sized geography runs on flights. That is not a secondary factor. It is the dataset.

### What's in the dataset

- Per-edition carbon totals from 2010–2026
- Scope breakdown where available (aviation vs. other sources)
- Methodology notes on accounting boundary differences between editions
- 2026 projection basis and source

→ [Read the full story](https://datahub.io/football/each-world-cups-carbon-footprint)

## Dataset 2: World Cup Prize Money

![[trophy.png]]

→ [worldcup-prize-money on DataHub](https://datahub.io/football/worldcup-prize-money)

The 2026 men's prize pool totals $655M — the largest in World Cup history. The winner takes $50M. Teams eliminated at the group stage earn $9M for qualifying and participating.

The winner's prize has increased at every edition without exception: $30M (2010) → $35M (2014) → $38M (2018) → $42M (2022) → $50M (2026). The trajectory is clean.

### The data quality problem this dataset solves

Two problems required explicit handling.

First, pre-2014 men's figures use a "total contribution" scope — a broader definition that includes payments beyond pure prize money. We label these clearly so users do not compare them directly to pure prize money figures from later editions.

Second, and more significant: we validated the 2022 per-team payouts by summing all 32 individual figures against the published pool total. They match exactly — $440M. This is not a trivial check. Widely circulated prize money figures frequently contain rounding errors or scope mismatches that only surface when you do the arithmetic.

### The gender gap in the data

The 2022 men's pool ($440M) was four times the 2023 Women's World Cup pool ($110M). Before 2007, women's prize money was zero — not a small number, literally absent. FIFA has committed to equal prize money by 2027. The dataset tracks both series so users can monitor that commitment against actual allocations.

### What's in the dataset

- Per-edition prize pools for men's and women's tournaments
- Per-team payouts for available editions (validated against pool totals)
- Scope flags on pre-2014 figures
- FIFA commitment timeline for gender parity

→ [Read the full story](https://datahub.io/football/42-million-to-win)

## Dataset 3: World Cup Ticket Prices

![[datahub-tickets.png]]

→ [worldcup-ticket-prices on DataHub](https://datahub.io/football/worldcup-ticket-prices)

The most expensive face-value ticket to the 2026 final is $10,990 — a 6.8× increase on the $1,607 top price in 2022. The cheapest official entry is $60 for a Supporter Entry tier. Resale prices for the final are running near $33,000.

On May 27, 2026, the attorneys general of New York and New Jersey subpoenaed FIFA over 2026 ticket pricing — the first time a major tournament host's law enforcement has taken formal legal action over World Cup prices. The affordability gap between cheapest and most expensive tickets has widened at every edition since 2010.

### The data quality problem this dataset solves

A widely-cited 2014 ticket price figure in circulation appears to reflect resale value rather than face value. Including it would produce a misleading historical comparison. We excluded it explicitly — not silently — and flagged the exclusion in the dataset notes. All figures are nominal, not inflation-adjusted; this is noted clearly so users who need real-terms comparisons can apply their own deflators.

Even inflation-adjusted, the 2026 jump holds.

### What's in the dataset

- Per-edition face-value price ranges (floor and ceiling) from 2006–2026
- Category breakdown where available
- Exclusion flags and methodology notes
- Nominal figures with inflation-adjustment guidance

## Why We Built These

[DataHub.io](https://datahub.io/) exists to publish high-quality, reusable open data — fully documented, methodologically honest, and downloadable without friction. The World Cup datasets are a case study in what that means in practice.

The underlying numbers for carbon, prize money, and ticket prices exist in FIFA reports, press releases, and news coverage. What does not exist — until now — is a single place where those numbers are placed on consistent definitional footing, cross-validated where possible, and published with explicit methodology notes rather than silent assumptions.

**These datasets are built for reuse.** Pull them into your own analysis pipeline, build your own charts, verify our methodology, or extend the series when 2026 final figures are published.

They join our [92-year World Cup results dataset](https://datahub.io/football/worldcup) published last month. All football datasets are collected at [datahub.io/football](https://datahub.io/football).

_[DataHub.io](https://www.datahub.io/) is a platform for high-quality open datasets — free to use, fully documented, and built for reuse. Built by [Datopian](https://www.datopian.com/)._
