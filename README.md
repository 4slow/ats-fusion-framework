# ATS Fusion — Public Framework

This repository is the **public framework** of an algorithmic trading system:
- execution engine + state management
- IBKR adapter (ib_insync)
- risk-first position sizing & gates
- logging + performance reporting

✅ **What this repo is:** infrastructure / framework proof.  
🚫 **What this repo is NOT:** the proprietary strategy edge.  
The real signal logic is intentionally **not** included. This repo ships with a **demo strategy** so it can run end-to-end.

## Quick start (Paper Trading)

1. Create a virtualenv and install deps:
```bash
pip install -r requirements.txt
```

2. Create a `main.env` file from the example:
```bash
cp main.env.example main.env
```

3. Run:
```bash
python -m src.core.bot_public
```

> ⚠️ Paper trading requires IB Gateway / TWS running and `ib_insync` connectivity.

## Repository layout

- `src/core/bot_public.py` – the runnable engine (public demo strategy included)
- `docs/ARCHITECTURE.md` – architecture overview
- `docs/RISK_MODEL.md` – risk model & gates
- `examples/` – examples and notes

## Security / hygiene

This repo **does not** include:
- API tokens (Telegram, etc.)
- live trading credentials
- proprietary signal logic

See `.gitignore` for excluded files.
