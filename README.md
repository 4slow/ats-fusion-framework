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
