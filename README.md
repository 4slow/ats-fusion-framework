# ATS Fusion — Public Trading Framework (Portfolio)

A **public** systematic-trading framework that demonstrates:
- clean, modular architecture (engine / indicators / risk / reporting)
- a simulation mode that runs **out-of-the-box** (no broker required)
- optional **IBKR TWS / IB Gateway** plumbing (proof of integration)

> **Important:** This repository intentionally ships with a **demo strategy only**.  
> Real alpha/edge (signal rules + tuned parameters) belongs in a **private repo**.

---

## What this repo is (and is not)

### ✅ Included (public)
- Simulation engine + sample dataset (`data/sample_prices.csv`)
- Strategy interface + **demo strategy** (EMA crossover)
- Risk & safety brakes (e.g., max drawdown stop)
- Reporting (PnL, trades, win rate, max drawdown)
- Optional IBKR adapter & live runner (TWS)

### ❌ Not included (private)
- Real entry/exit logic (your alpha/edge)
- Tuned parameters that create a market advantage
- Private configs/secrets (`.env` is ignored)

---

## Quick start (no TWS)

### 1) Install
```bash
python -m pip install -r requirements.txt
```

### 2) Run simulation
```bash
python -m src
```

You should see a summary like:
- Final equity
- Total PnL
- Number of trades
- Win rate
- Max drawdown

---

## Optional: Live mode (IBKR TWS / IB Gateway)

### Safety note
Live mode exists as **proof-of-plumbing** only:
- Uses the **demo strategy** (not edge)
- Uses **tiny order sizes** by default (intentionally)

### 1) TWS setup
In TWS / IB Gateway:
- Enable API connections
- Allow connections from `127.0.0.1`
- Set API port (Paper is commonly `7497`, Live is commonly `7496`)

### 2) Configure environment
Copy `.env.example` → `.env` and edit:
- `IBKR_HOST`
- `IBKR_PORT`
- `IBKR_CLIENT_ID`
- `LIVE_SYMBOL` (e.g., SPY)

> `.env` is ignored by git for safety.

### 3) Run live runner
```bash
python -m src.core.live_engine
```

Docs:
- `docs/IBKR_SETUP.md`

---

## Project structure

```
ats-fusion-framework/
  src/
    core/
      sim_engine.py        # simulation entrypoint
      live_engine.py       # optional IBKR/TWS runner
      engine.py            # core trading loop (simulation)
      indicators.py        # EMA/ATR, etc.
      risk.py              # sizing & risk brakes
      reporting.py         # summary output
      datafeed.py          # CSV loader
    strategies/
      base.py              # strategy interface
      demo_ema_cross.py    # public demo strategy
    adapters/
      ibkr.py              # IBKR adapter (ib_insync)
  data/
    sample_prices.csv
  docs/
    ARCHITECTURE.md
    RISK_MODEL.md
    IBKR_SETUP.md
  .env.example
  requirements.txt
  LICENSE
```

---

## How to plug in a private strategy (recommended)

Keep your real strategy in a private repo and plug it in via the strategy interface
(e.g., implement a `generate_signal(df)` method). This keeps the public repo as
a clean portfolio proof while protecting the edge.

---

## License
MIT (see `LICENSE`).
