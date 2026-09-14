# Cloud Storage Cost Calculator

**[▶ Live demo](https://shubhamkumbhalkar.github.io/bee-cloud-cost-calculator/)**

An interactive calculator that compares what you'll pay a cloud storage subscription over time
against buying storage once and owning it. Move three sliders, get your total spend, your savings,
your payback period, and the exact month ownership pulls ahead.

One file. No build step. No dependencies. No backend, no tracking — every calculation runs in
your browser.

```
index.html   ← the entire application (HTML + CSS + JS)
```

## Why

Storage subscriptions are priced to feel small: $9.99 here, $11.99 there. The number that
actually matters is the one nobody shows you — the cumulative total, and the point at which a
one-time purchase would already have paid for itself. This makes that crossover visible.

## Features

- **Three inputs that matter** — monthly spend, household size, time horizon
- **Presets** for common plans (iCloud+, Google One, Dropbox) and stacked-subscription households
- **Any device price** — 4TB, 8TB, or a custom figure for whatever drive or NAS you're pricing
- **Break-even marker** plotted directly on the cumulative-cost chart
- **Electricity included** — ownership is charged ~$15/year in power, because ignoring it would
  stack the deck
- **Shareable URLs** — all state serialises to the query string, so any result is a link
- **Hand-rolled SVG chart** — no charting library, ~40 lines of JS
- **Accessible** — labelled controls, `aria-live` results, keyboard-operable, honours
  `prefers-reduced-motion`
- **Responsive** — single-column below 900px

## The model

| | Formula |
|---|---|
| Subscription | `monthly × 12 × years` |
| Ownership | `price + (10W ÷ 1000 × 24 × 365 × years × $0.17/kWh)` |
| Break-even | `price ÷ (monthly − monthly power cost)` |

Assumes 10 W idle draw and $0.17/kWh (roughly the US residential average), so about $15/year in
electricity.

**Deliberately excluded**, and the app says so in its own methodology panel:

- Drive replacement over long horizons — a 10-year window realistically includes one
- An off-site copy, since owning a device is not by itself a backup strategy (3-2-1 needs a
  second copy elsewhere, which may reintroduce a small recurring cost)
- Price inflation on either side, and hardware resale value

Subscription prices are US list prices at time of writing. Treat the output as
order-of-magnitude, not a quote — the useful signal is *how early* the crossover lands, not the
exact dollar figure.

## Run it locally

No tooling required — open the file:

```bash
open index.html
```

Or serve it, if you want the shareable-URL behaviour to work exactly as deployed:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Deploy

Any static host works. For GitHub Pages: push to `main`, then
**Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**.

## License

MIT — see [LICENSE](LICENSE).
