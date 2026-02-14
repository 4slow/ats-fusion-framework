# ATS Fusion — Public Framework (Runnable Without TWS)

This repository is the **public framework** of an algorithmic trading system:
- brokerless **simulation/backtest engine** (no TWS / IB Gateway required)
- **risk-first** gates (ATR sizing + max drawdown brake)
- clean separation between **framework (public)** and **strategy edge (private)**

✅ **What this repo is:** infrastructure / framework proof.  
🚫 **What this repo is NOT:** the proprietary strategy edge.

The real signal logic is intentionally **not** included. This repo ships with a **demo strategy** so it can run end-to-end.

---

## Quick start (Simulation — no broker required)

```bash
pip install -r requirements.txt
python -m src
```

This runs a demo EMA-cross strategy on the included dataset (`data/sample_prices.csv`) and prints a summary.

---

## CLI usage (recommended)

Override parameters:
```bash
python -m src --data data/sample_prices.csv --risk 250 --max-dd 12 --ema-fast 30 --ema-slow 150
```

Save outputs:
```bash
python -m src --out-json out/summary.json --out-trades-csv out/trades.csv
```

Use your own dataset (CSV required columns minimum):
`date, open, high, low, close` (optional: `volume`)

---

## Tests

```bash
pip install -r requirements-dev.txt
pytest
```

A GitHub Actions workflow is included under `.github/workflows/tests.yml`.

---

## Project layout

- `src/core/engine.py` — backtest engine (framework)
- `src/core/risk.py` — ATR sizing + drawdown brake
- `src/core/indicators.py` — minimal EMA/ATR helpers
- `src/core/reporting.py` — summary + trades export
- `src/strategies/demo_ema_cross.py` — demo strategy (NOT edge)
- `data/sample_prices.csv` — sample OHLCV so anyone can run
- `docs/ARCHITECTURE.md` — architecture overview
- `docs/RISK_MODEL.md` — risk-first model & gates

---

## Security / what is intentionally excluded

- proprietary strategy rules, parameters, and edge logic
- tokens, account IDs, state files, logs

See `.gitignore` and `main.env.example`.

---

## Optional: IBKR / Paper Trading (not required)

The repository includes a legacy IBKR-oriented script (`src/core/bot_public.py`) as a reference.
It is **not** required for the simulation flow and may require additional setup (TWS/IB Gateway).


## Run modes

- **Simulation (default)**: `python -m src --mode sim`
- **Live (IBKR/TWS)**: `python -m src --mode live`

See `docs/IBKR_SETUP.md` for TWS configuration.
