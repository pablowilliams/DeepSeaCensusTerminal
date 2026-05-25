# DeepSeaCensusTerminal

Terminal-style species-accumulation Monte Carlo dashboard for deep-sea biodiversity: bathyal/abyssal/hadal clade richness, depth-pressure profiling, and Chao1 / ACE non-parametric estimators.

## Features

- **Monte Carlo simulation** — Geometric Brownian Motion engine, configurable paths (100 / 1k / 10k) and horizons (5 / 30 / 90 / 252 periods).
- **Clade watchlist** — 12 clades (POLY, ISOP, FORAM, GASTRO, ECHIN…).
- **Live tick simulation** — synthetic ticks every few seconds with deterministic seed for reproducibility.
- **Strategy signals** — ENDEMIC / INVASIVE / STABLE derived from Discovery MA Cross, Sampling MR, Range Momentum, Chao1 Skew, Biologist Notes.
- **DSC chatter panel** — positive / neutral / negative sentiment with sample posts per clade.
- **Clade KPIs** — aggregate value, P&L, expected return, 95% VaR, Sharpe, sentiment.
- **Custom panel** — domain-specific panel.
- **Accessible by default** — WCAG 2.2 AA: keyboard nav, ARIA live regions, screen-reader chart alternatives, 4.5:1 contrast in dark mode.

## Running

No build step. Live at https://pablowilliams.github.io/DeepSeaCensusTerminal/.

For local development, any static server works:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Data pipeline

The dashboard reads `data/quotes.json` on load and on each tick. A scheduled GitHub Action (`.github/workflows/refresh-data.yml`) regenerates synthetic close histories every hour so the visible data evolves. Replace the generator with a real data source to go live.

## Architecture

- `index.html` — semantic layout, landmarks, headings
- `app.js` — data, Monte Carlo engine, sentiment, signal logic, rendering
- `styles.css` — dark terminal theme with AA-contrast tokens

## License

Private. All rights reserved.
