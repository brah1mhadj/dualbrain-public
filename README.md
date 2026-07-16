<div align="center">

<img src="https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
<img src="https://img.shields.io/badge/Status-LIVE-e74c3c?style=for-the-badge" alt="Status">
<img src="https://img.shields.io/badge/License-MIT-2ecc71?style=for-the-badge" alt="License">
<img src="https://img.shields.io/badge/Strategies-66+-9b59b6?style=for-the-badge" alt="Strategies">
<img src="https://img.shields.io/badge/Tests-64%2F64%20Pass-27ae60?style=for-the-badge" alt="Tests">

<br>
<br>

# DualBrain

### Autonomous AI Trading Engine with Dialectical Reasoning

A trading system where two language models debate every decision — a creative **Explorer** proposes, a skeptical **Guardian** challenges, and only consensus becomes action.

<br>

</div>

---

## How It Works

DualBrain replaces single-model trading bots with a **dialectical architecture**: two specialized LLMs engage in structured debate before any trade is placed.

```
         ┌─────────────────────────────────────────┐
         │            Market Data Input             │
         └──────────────────┬──────────────────────┘
                            │
                ┌───────────┴───────────┐
                ▼                       ▼
        ┌──────────────┐       ┌──────────────┐
        │   Θ THETA    │       │  Ε EPSILON   │
        │   Explorer   │◄─────►│   Guardian   │
        │  (Creative)  │ debate │  (Skeptical) │
        └──────┬───────┘       └──────┬───────┘
               │                      │
               └──────────┬───────────┘
                          ▼
                ┌──────────────────┐
                │    SYNTHESIS     │
                └────────┬─────────┘
                         ▼
              ┌─────────────────────┐
              │  10-Factor Signal   │──► 60%+ consensus required
              │      Engine         │
              └────────┬────────────┘
                       ▼
              ┌─────────────────────┐
              │   Risk Validation   │──► 7 safety checks
              └────────┬────────────┘
                       ▼
              ┌─────────────────────┐
              │   MT5 Execution     │──► ATR-based SL/TP
              └────────┬────────────┘
                       ▼
              ┌─────────────────────┐
              │   Memory + Alerts   │──► Telegram notifications
              └─────────────────────┘
```

Every trade passes through **three layers**:

| Layer | What It Does | Failure Mode |
|-------|-------------|--------------|
| **Signal Engine** | 10-factor technical consensus | No consensus → HOLD |
| **Risk Manager** | Margin, drawdown, position sizing | Violation → BLOCK |
| **Dialectical Approval** | Theta ↔ Epsilon debate | Disagreement → REJECT |

---

## Architecture

```
dualbrain/
├── orchestrator.py          # Core dialectical cycle engine
├── theta.py                 # Θ Explorer — creative, divergent
├── epsilon.py               # Ε Guardian — analytical, skeptical
├── llm_client.py            # OpenAI-compatible client + fallback chain
├── memory.py                # TripleMemory — episodic + semantic + procedural
├── dream.py                 # DreamEngine — async memory consolidation
├── tools.py                 # ToolBox — 38 permission-gated tools
├── config.py                # Centralized configuration
│
├── autonomous_trader.py     # Complete autonomous trading loop
├── signal_engine.py         # 10-factor consensus generator
├── data_feeds.py            # MT5 + TradingView + Web aggregation
├── trade_approval.py        # Dialectical trade approval
├── telegram_alerts.py       # Real-time notifications
├── market_hours.py          # Trading session detection
│
├── strategy_lab.py          # Backtesting engine
├── advanced_strategies.py   # 12 strategy classes
├── strategy_v2.py           # 16 V2 strategies
├── hybrid_strategies.py     # 20 ICT/SMC hybrids
├── ict_strategies.py        # 8 institutional ICT/SMC
├── strategy_expansion.py    # 20 expansion strategies
├── param_optimizer.py       # Grid search + composite ranking
├── research_scheduler.py    # Daily autonomous research
│
├── tradingview_scraper.py   # TradingView data via Playwright
├── obsidian_bridge.py       # Obsidian → TripleMemory
├── mcp_acp.py               # MCP/ACP inter-agent server
│
├── main.py                  # CLI — REPL, queries, status
├── test_offline.py          # 64-test offline suite
├── test_smoke.py            # Live smoke test
├── test_integration.py      # Full integration tests
│
└── memory/
    ├── episodic/            # Interaction logs, trade outcomes
    ├── semantic/            # Patterns (Theta's domain)
    └── procedural/          # Gotchas (Epsilon's domain)
```

---

## Signal Engine

Ten independent factors vote on every candle. A trade requires **60%+ agreement**.

| # | Factor | Source | Weight | Block Rule |
|---|--------|--------|--------|------------|
| 1 | RSI(14) | MT5 candles | 1.2x | — |
| 2 | Bollinger Bands | MT5 candles | 1.0x | — |
| 3 | SMA Crossover | MT5 candles | 1.0x | — |
| 4 | MACD | MT5 candles | 1.0x | — |
| 5 | Stochastic | MT5 candles | 1.0x | — |
| 6 | Alpha Signals | VibeBridge | 1.0x | — |
| 7 | News Sentiment | Google News RSS | 1.0x | — |
| 8 | Fear & Greed | CNN / alt.me / VIX | 1.0x | — |
| 9 | Economic Calendar | Faireconomy API | 2.0x | HIGH impact → HOLD |
| 10 | Account Risk | MT5 account | 3.0x | Margin <10% → BLOCK |

Signal strength tiers: **STRONG** (>70%), **MODERATE** (>50%), **WEAK** (<50%).

---

## The Dialectical Engine

Two models with complementary personalities:

| | Theta (Explorer) | Epsilon (Guardian) |
|---|---|---|
| **Role** | Generate ideas, spot patterns | Challenge assumptions, find risks |
| **Temperature** | 0.8 (creative, divergent) | 0.2 (analytical, convergent) |
| **Style** | "Here's what I see — let's act" | "Here's what's wrong — let's wait" |
| **Default Model** | mimo-v2.5-free | big-pickle |

### Example Debate

```
Theta:  "RSI oversold at 28, Bollinger below lower band. BUY signal."
Epsilon: "NFP in 30 minutes. Wait — or reduce size to 0.01 lots."

Theta:  "NFP at 12:30 UTC, it's 11:00 now. We have 90 minutes."
Epsilon: "Agreed. Enter with tight 1.5x ATR stop loss."

→ CONSENSUS: BUY with reduced position and tight SL
```

Debate stops when:
- Both models agree (>50% content-word overlap)
- Max rounds reached (default: 2)
- Either raises an unresolvable concern

---

## Triple Memory System

Every interaction is processed through three memory stores:

| Store | Domain | Content |
|-------|--------|---------|
| **Episodic** | What happened | Trade outcomes, conversation logs |
| **Semantic** | Patterns | Insights extracted by Theta |
| **Procedural** | Gotchas | Risks and workflows extracted by Epsilon |

After each cycle, the **DreamEngine** runs asynchronously:
1. Theta scans the interaction → extracts a pattern → writes to semantic memory
2. Epsilon scans the interaction → extracts a risk → writes to procedural memory
3. Memories accumulate and influence future decisions

---

## Quick Start

### Requirements

- Python 3.12+
- OpenAI-compatible LLM endpoint (default: `http://127.0.0.1:5200/v1`)
- MetaTrader 5 terminal (for live trading)

### Install

```bash
git clone https://github.com/brah1mhadj/dualbrain.git
cd dualbrain
pip install httpx numpy pandas MetaTrader5
```

### Configure

All settings in `config.py`:

```python
LLM_BASE_URL = "http://127.0.0.1:5200/v1"
THETA_MODEL  = "mimo-v2.5-free"
EPSILON_MODEL = "big-pickle"
MAX_DIALECTICAL_ROUNDS = 2
MAX_EXECUTION_STEPS = 15
```

### Run

```bash
# Interactive REPL
python main.py

# Single query
python main.py "What's the current XAUUSD trend?"

# System status
python main.py --status

# Search memory
python main.py --search "gold trading"
```

---

## Autonomous Trading

```bash
# Single scan
python autonomous_trader.py --once

# Continuous loop (default: 5-min intervals)
python autonomous_trader.py --loop

# Dry run — analyze, don't trade
python autonomous_trader.py --once --dry-run

# Custom symbol/timeframe
python autonomous_trader.py --once --symbol XAUUSD --timeframe H1
```

### Decision Flow

```
1. COLLECT    MT5 quotes, TradingView analysis, news, fear index
2. ANALYZE    10-factor signal engine → consensus score
3. VALIDATE   7 risk checks (margin, drawdown, position count, cooldown)
4. DEBATE     Theta ↔ Epsilon structured argument
5. EXECUTE    ATR-based SL/TP, 2% risk per trade
6. RECORD     Telegram alert + TripleMemory storage
```

### Risk Parameters

| Parameter | Value |
|-----------|-------|
| Max drawdown | 15% (auto-stop) |
| Risk per trade | 2% of balance |
| Max positions | 3 simultaneous |
| Daily loss limit | 5% of balance |
| Position sizing | Fixed fractional (2% risk) |

---

## Strategy Lab

**66+ strategies** across four categories:

| Category | Count | Examples |
|----------|-------|----------|
| Traditional | 38 | RSI Mean Reversion, Bollinger Squeeze, MACD Trend, Ichimoku Cloud, VWAP, Parabolic SAR |
| ICT/SMC | 13 | Order Block, Fair Value Gap, BOS/CHoCH, Liquidity Sweep, Kill Zone |
| Hybrid/Ensemble | 20 | FVG + Bollinger, OB + RSI, Multi-Factor Ensemble, Regime-Adaptive |
| Multi-Timeframe | 5 | MTF Trend Align, MTF RSI Divergence, MTF Breakout Cascade |

```bash
# Backtest all strategies on XAUUSD H1
python -c "
from strategy_lab import load_mt5_data, backtest_all
data = load_mt5_data('XAUUSD', 'H1', 5000)
results = backtest_all(data)
for name, score in results.ranking[:5]:
    print(f'{name}: {score:.2f}')
"

# Optimize parameters
python -c "from param_optimizer import optimize_all; print(optimize_all('XAUUSD', 'H1'))"

# Daily research cycle
python research_scheduler.py
```

---

## Telegram Alerts

| Alert | Trigger |
|-------|---------|
| Trade opened/closed | Every execution |
| Signal generated | Every analysis cycle |
| Drawdown warning | >8% drawdown |
| Drawdown critical | >15% drawdown |
| Economic event | HIGH impact imminent |

Rate limited (1s minimum) and deduplicated (5min cooldown per type).

---

## Tool System

**38 tools** for Theta (full access), **17 read-only** for Epsilon:

| Category | Theta | Epsilon |
|----------|-------|---------|
| File operations | read, write, delete, move, search, grep, download | read, search, grep |
| System | info, processes, env | info, processes, env |
| Web | get, search | get, search |
| Terminal | run, python | — |
| Browser | open, close, click, type, screenshot, extract | screenshot, extract |
| Desktop | screenshot, mouse, keyboard | screenshot |
| Communication | email send, telegram send | email read |
| Clipboard | read, write | read |
| App/Window | launch, kill, list, focus, close | list |

---

## Testing

```bash
# 64 offline tests (no LLM required)
python test_offline.py

# Live smoke test (requires LLM proxy)
python test_smoke.py

# Full integration
python test_integration.py
```

Coverage: config validation, ToolBox dispatch, TripleMemory CRUD, SignalEngine analysis, market hours, trade approval, strategy loading, DreamEngine processing, LLMClient fallbacks.

---

## Deployment

### Background Process

```bash
start /B python autonomous_trader.py --loop --interval 1800 --log-level INFO
```

### Scheduled (QwenPaw Cron)

```bash
qwenpaw cron create \
  --name "autonomous-trader" \
  --schedule "*/30 * * * *" \
  --command "python autonomous_trader.py --once" \
  --agent-id evilagent
```

### Monitoring

```bash
tail -f autonomous_trader.log
python main.py --memory
```

---

## Dependencies

| Package | Required | Purpose |
|---------|----------|---------|
| `httpx` | Yes | HTTP client for LLM + APIs |
| `numpy` | Yes | Strategy calculations |
| `pandas` | Yes | Data manipulation |
| `MetaTrader5` | Yes | Live trading |
| `backtesting` | Optional | Strategy backtesting |
| `playwright` | Optional | TradingView scraping |

---

## Model Benchmarking

Benchmarked 2026-07-15 across creative, analytical, and fast queries:

| Model | Speed | Quality | Reliability | Role |
|-------|-------|---------|-------------|------|
| **mimo-v2.5-free** | 10-13s | Excellent | 5/5 | Theta (Explorer) |
| **big-pickle** | 9-13s | Very Good | 4/5 | Epsilon (Guardian) |
| nemotron-3-ultra-free | 3-8s | Good | 5/5 | Fallback |
| north-mini-code-free | 4-6s | Good | 5/5 | Fallback |

---

## Configuration Reference

| Setting | Default | Description |
|---------|---------|-------------|
| `LLM_BASE_URL` | `http://127.0.0.1:5200/v1` | API endpoint |
| `THETA_MODEL` | `mimo-v2.5-free` | Explorer model |
| `EPSILON_MODEL` | `big-pickle` | Guardian model |
| `THETA_TEMPERATURE` | `0.8` | Explorer creativity |
| `EPSILON_TEMPERATURE` | `0.2` | Guardian skepticism |
| `MAX_DIALECTICAL_ROUNDS` | `2` | Debate cycles |
| `MAX_EXECUTION_STEPS` | `15` | Max tool calls |
| `CONVERGENCE_THRESHOLD` | `0.50` | Agreement threshold |

---

<div align="center">

**Built by [Hadj](https://github.com/brah1mhadj)**

*Two minds. One decision. Zero hesitation.*

<br>

<img src="https://img.shields.io/badge/Exness-MT5-1a73e8?style=for-the-badge&logo=chartline&logoColor=white" alt="MT5">
<img src="https://img.shields.io/badge/LLM-OpenAI%20Compatible-412991?style=for-the-badge&logo=openai&logoColor=white" alt="LLM">
<img src="https://img.shields.io/badge/Platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white" alt="Windows">

</div>
