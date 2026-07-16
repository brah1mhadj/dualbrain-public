<div align="center">

# ⚡ DUALBRAIN v4

### *Two Minds. One Decision. Zero Hesitation.*

**An autonomous AI trading system powered by dialectical reasoning — where a creative Explorer and a skeptical Guardian debate every decision before a single pip is risked.**

[![Python 3.12+](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-LIVE-brightred.svg)](#quick-start)

</div>

---

## 🧠 What Is This?

DualBrain is not another "buy when RSI < 30" bot. It's a **dialectical AI architecture** where two specialized language models engage in structured debate before every trading decision:

```
         ┌─────────────────────────────────────────────────┐
         │                  USER REQUEST                    │
         └──────────────────────┬──────────────────────────┘
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
                    ┌──────────────────┐
                    │  TOOL EXECUTION  │
                    └────────┬─────────┘
                             ▼
                    ┌──────────────────┐
                    │   DREAM CYCLE    │
                    │  (Memory Learn)  │
                    └──────────────────┘
```

The system then feeds this through a **10-factor signal engine** (RSI, MACD, Bollinger, Stochastic, News Sentiment, Fear & Greed, Economic Calendar, Alpha Signals, Account Risk, SMA Crossover) — requiring **60%+ consensus** before any trade is placed.

**Every trade goes through 3 layers of validation:**
1. **Signal Engine** — multi-factor technical consensus
2. **Risk Manager** — 7 safety checks (margin, drawdown, position sizing)
3. **Dialectical Approval** — Theta and Epsilon debate the trade itself

---

## 📁 Architecture

```
dualbrain/
├── orchestrator.py          # 🧠 Main brain — dialectical cycle engine
├── theta.py                 # Θ Explorer — creative, divergent, fast
├── epsilon.py               # Ε Guardian — analytical, skeptical, careful
├── llm_client.py            # OpenAI-compatible client with model fallback
├── memory.py                # TripleMemory — episodic + semantic + procedural
├── dream.py                 # DreamEngine — async memory consolidation
├── tools.py                 # ToolBox — 38 permission-gated tools
├── config.py                # All configuration in one place
│
├── autonomous_trader.py     # 🤖 The complete autonomous trading system
├── signal_engine.py         # 10-factor consensus signal generator
├── data_feeds.py            # MT5 + TradingView + Web data aggregation
├── risk_manager.py          # Position sizing & risk validation (in autonomous_trader)
├── trade_approval.py        # Dialectical trade approval (Theta ↔ Epsilon)
├── telegram_alerts.py       # Real-time Telegram notifications
├── market_hours.py          # Trading session detection (XAUUSD hours)
│
├── strategy_lab.py          # Backtesting engine (10 strategies)
├── advanced_strategies.py   # 12 additional strategy classes
├── strategy_v2.py           # 16 V2 strategies (trend, mean-reversion, breakout)
├── hybrid_strategies.py     # 20 ICT/SMC + traditional hybrids
├── ict_strategies.py        # 8 institutional-grade ICT/SMC strategies
├── strategy_expansion.py    # 20 more strategies (32 total from expansion)
├── param_optimizer.py       # Grid search & composite ranking
├── research_scheduler.py    # Daily autonomous research (backtest + optimize)
│
├── tradingview_scraper.py   # TradingView chart data via Playwright
├── obsidian_bridge.py       # Obsidian vault → TripleMemory integration
├── mcp_acp.py               # MCP/ACP server for inter-agent communication
│
├── main.py                  # 🖥️  CLI interface — REPL, single query, status
├── test_offline.py          # 64-test offline infrastructure suite
├── test_smoke.py            # Live smoke test (requires LLM proxy)
├── test_integration.py      # Full integration tests
├── full_test.py             # Comprehensive test runner
│
└── memory/                  # 💾 Triple memory stores
    ├── episodic/            # What happened (interaction logs)
    ├── semantic/            # Patterns & connections (Theta's domain)
    └── procedural/          # Gotchas & workflows (Epsilon's domain)
```

---

## ⚡ Quick Start

### Prerequisites

- **Python 3.12+**
- **OpenCode jailbroken proxy** running on `http://127.0.0.1:5200` (or any OpenAI-compatible endpoint)
- **MT5 Terminal** with Exness account (for live trading)

### Installation

```bash
# Clone the repository
git clone <your-repo-url> dualbrain
cd dualbrain

# Install dependencies
pip install httpx numpy pandas

# For backtesting (optional)
pip install backtesting

# For browser automation (optional)
pip install playwright
playwright install chromium

# For desktop control (optional)
pip install pyautogui pyperclip pygetwindow mss
```

### Configuration

All configuration lives in `dualbrain/config.py`. Key settings:

```python
# LLM Backend
LLM_BASE_URL = "http://127.0.0.1:5200/v1"  # OpenCode proxy
LLM_API_KEY = ""                             # No auth needed for local

# Model Assignment (benchmarked)
THETA_MODEL = "mimo-v2.5-free"     # Explorer — creative, 10-13s, 1160-1260 chars
EPSILON_MODEL = "big-pickle"       # Guardian — analytical, 9-13s, up to 1300 chars

# Fallback Chain (tried on failure)
THETA_MODEL_FALLBACKS = ["nemotron-3-ultra-free", "north-mini-code-free"]
EPSILON_MODEL_FALLBACKS = ["nemotron-3-ultra-free", "north-mini-code-free"]

# Trading
MAX_DIALECTICAL_ROUNDS = 2    # Thesis → Antithesis → Synthesis cycles
MAX_EXECUTION_STEPS = 15      # Max tool calls per execution
```

### Run

```bash
# Interactive REPL
python dualbrain/main.py

# Single query
python dualbrain/main.py "What's the current XAUUSD trend?"

# System status
python dualbrain/main.py --status

# Browse memory
python dualbrain/main.py --memory

# Run dream cycle
python dualbrain/main.py --dream

# Search memory
python dualbrain/main.py --search "gold trading"
```

---

## 🤖 Autonomous Trading System

The main event. A fully autonomous trading loop that runs every 30 minutes:

### Run Modes

```bash
# Single scan — analyze and optionally trade
python dualbrain/autonomous_trader.py --once

# Continuous loop — default 5-minute intervals
python dualbrain/autonomous_trader.py --loop

# Custom interval (every 30 minutes)
python dualbrain/autonomous_trader.py --loop --interval 1800

# Dry run — analyze but don't trade
python dualbrain/autonomous_trader.py --once --dry-run

# Research mode — scan GitHub + YouTube for new strategies
python dualbrain/autonomous_trader.py --research

# Custom symbol/timeframe
python dualbrain/autonomous_trader.py --once --symbol XAUUSD --timeframe H1
```

### Decision Flow (Every Cycle)

```
┌─────────────────────────────────────────────────────────────┐
│  1. DATA COLLECTION                                         │
│     ├── MT5: live quotes, candles, positions, account       │
│     ├── TradingView: technical analysis summary             │
│     ├── Web: economic calendar, news sentiment, F&G index   │
│     └── VibeBridge: custom alpha signals                    │
├─────────────────────────────────────────────────────────────┤
│  2. SIGNAL GENERATION (10-Factor Consensus)                 │
│     ├── RSI(14) ─── BUY if <30, SELL if >70                │
│     ├── Bollinger ── BUY below lower, SELL above upper      │
│     ├── SMA Cross ── BUY if price > SMA20 > SMA50          │
│     ├── MACD ─────── BUY if >0, SELL if <0                 │
│     ├── Stochastic ─ BUY if K<20, SELL if K>80             │
│     ├── Alpha Signals from VibeBridge                       │
│     ├── News Sentiment (keyword scoring)                    │
│     ├── Fear & Greed (CNN → alternative.me → VIX)           │
│     ├── Economic Calendar (HIGH impact = PAUSE)             │
│     └── Account Risk (margin level, drawdown)               │
├─────────────────────────────────────────────────────────────┤
│  3. RISK VALIDATION (7 Checks)                              │
│     ├── ✓ Position count ≤ 3                                │
│     ├── ✓ Free margin > 30%                                 │
│     ├── ✓ Not in cooldown                                   │
│     ├── ✓ Daily loss < 5%                                   │
│     ├── ✓ Max drawdown < 15%                                │
│     ├── ✓ Signal strength ≥ MODERATE                        │
│     └── ✓ No blocking economic event                        │
├─────────────────────────────────────────────────────────────┤
│  4. DIALECTICAL TRADE APPROVAL                              │
│     ├── Theta argues FOR the trade (opportunity, edge)      │
│     ├── Epsilon argues AGAINST (risk, timing, drawdown)     │
│     └── → APPROVE / REJECT / MODIFY (resize)               │
├─────────────────────────────────────────────────────────────┤
│  5. EXECUTION                                               │
│     ├── Calculate SL/TP via ATR (1.5x SL, 3x TP)           │
│     ├── Calculate position size (2% risk per trade)         │
│     └── Execute on MT5 via order_send()                     │
├─────────────────────────────────────────────────────────────┤
│  6. POST-TRADE                                              │
│     ├── Telegram alert (trade opened/closed)                │
│     ├── Drawdown monitoring + alerts                        │
│     └── TripleMemory: record outcome for learning           │
└─────────────────────────────────────────────────────────────┘
```

---

## 🧠 The Dialectical Engine

The core innovation: **two AI models debate before every decision**.

### Theta (Explorer)
- **Model:** mimo-v2.5-free
- **Temperature:** 0.8 (creative, divergent)
- **Role:** Generate ideas, propose actions, see patterns
- **Style:** Direct, concrete proposals, no philosophy

### Epsilon (Guardian)
- **Model:** big-pickle
- **Temperature:** 0.2 (analytical, convergent)
- **Role:** Challenge assumptions, spot risks, ensure quality
- **Style:** "Here's what's wrong, here's how to fix it"

### Debate Cycle

```
Round 1:
  Theta: "I see RSI oversold at 28, BB below lower band. BUY signal."
  Epsilon: "But there's a HIGH-impact NFP event in 30 minutes. WAIT."

Round 2:
  Theta: "NFP is at 12:30 UTC, it's 11:00 now. We have 90 minutes."
  Epsilon: "Agreed — enter with reduced size (0.01 lots) and tight SL."

→ CONSENSUS: BUY with modifications
```

The system stops debating when:
- Both agree (convergence threshold > 50% content-word overlap)
- Maximum rounds reached (2)
- Either raises an unresolvable concern

---

## 💾 Triple Memory System

DualBrain learns from every interaction through three specialized memory stores:

### Episodic Memory (`memory/episodic/`)
What happened — raw interaction logs, trade outcomes, conversation history.

### Semantic Memory (`memory/semantic/`)
Patterns and connections — insights extracted by Theta during the dream cycle.

### Procedural Memory (`memory/procedural/`)
Gotchas and workflows — risks and best practices extracted by Epsilon.

### Dream Cycle

After each dialectical cycle, the DreamEngine runs in the background:

1. **Theta** scans the interaction → extracts a pattern/insight → stores in semantic memory
2. **Epsilon** scans the interaction → extracts a risk/gotcha → stores in procedural memory
3. Over time, these memories accumulate and influence future decisions

```python
# Manual dream run
python dualbrain/main.py --dream

# Check memory stats
python dualbrain/main.py --memory

# Search memory
python dualbrain/main.py --search "RSI strategy"
```

---

## 🔧 Tool System

DualBrain has **38 tools** available to Theta (Explorer) and **17 read-only tools** for Epsilon (Guardian):

### Theta Tools (Full Access)
| Category | Tools |
|----------|-------|
| **File Operations** | `file_read`, `file_write`, `file_list`, `file_delete`, `file_move`, `file_search`, `file_grep`, `file_download` |
| **System** | `system_info`, `system_processes`, `system_env` |
| **Web** | `web_get`, `web_search` |
| **Terminal** | `terminal_run`, `terminal_python` |
| **Browser** | `browser_open`, `browser_close`, `browser_click`, `browser_type`, `browser_screenshot`, `browser_extract` |
| **Desktop** | `desktop_screenshot`, `desktop_mouse_move`, `desktop_mouse_click`, `desktop_key_press`, `desktop_type` |
| **Communication** | `email_send`, `telegram_send` |
| **Clipboard** | `clipboard_read`, `clipboard_write` |
| **App/Window** | `app_launch`, `app_kill`, `app_list`, `window_list`, `window_focus`, `window_close` |

### Epsilon Tools (Read-Only)
| Category | Tools |
|----------|-------|
| **File Operations** | `file_read`, `file_list`, `file_search`, `file_grep` |
| **System** | `system_info`, `system_processes`, `system_env` |
| **Web** | `web_get`, `web_search` |
| **Browser** | `browser_screenshot`, `browser_extract` |
| **Desktop** | `desktop_screenshot` |
| **Communication** | `email_read` |
| **Clipboard** | `clipboard_read` |
| **App/Window** | `app_list`, `window_list` |
| **Meta** | `list_tools` |

---

## 📊 Signal Engine

The 10-factor consensus system that drives all trading decisions:

| # | Factor | Data Source | Weight |
|---|--------|-------------|--------|
| 1 | **RSI(14)** | MT5 candles | 1.2× (oversold/overbought) |
| 2 | **Bollinger Bands** | MT5 candles | 1.0× |
| 3 | **SMA Crossover** | MT5 candles | 1.0× |
| 4 | **MACD** | MT5 candles | 1.0× |
| 5 | **Stochastic** | MT5 candles | 1.0× |
| 6 | **Alpha Signals** | VibeBridge | 1.0× |
| 7 | **News Sentiment** | Google News RSS | 1.0× |
| 8 | **Fear & Greed** | CNN → alt.me → VIX | 1.0× |
| 9 | **Economic Calendar** | Faireconomy API | 2.0× (HIGH impact = BLOCK) |
| 10 | **Account Risk** | MT5 account info | 3.0× (margin < 10% = BLOCK) |

**Consensus Requirements:**
- 60%+ of factors must agree on direction
- HIGH-impact economic events = automatic HOLD
- Margin free < 10% = automatic BLOCK
- Signal strength: STRONG (>70% confidence) / MODERATE (>50%) / WEAK (<50%)

---

## 📈 Strategy Lab

**66+ backtested strategies** across 4 categories:

### Traditional (10 + 12 + 16 = 38 strategies)
RSI Mean Reversion, Bollinger Squeeze, MACD Trend, Dual Thrust, EMA Ribbon, Stochastic RSI, ATR Channel, Heikin-Ashi, Volume Profile, Keltner Channel, Donchian Channel, Ichimoku Cloud, VWAP, Parabolic SAR, ADX, Coppock Curve, Williams %R, Chaikin Money Flow, ROC, Triple EMA + ADX, and more.

### ICT/SMC (8 + 5 = 13 strategies)
Order Block Reversal, Fair Value Gap, BOS/CHoCH Trend, Liquidity Sweep, Kill Zone Session, Market Structure Shift, Premium/Discount, ICT Confluence, Silver Bullet, Optimal Trade Entry, Institutional Order Flow, Displacement Reversal, Liquidity Void Fill.

### Hybrid/Ensemble (20 strategies)
FVG + Bollinger, Order Block + RSI, BOS + EMA Ribbon, Liquidity Sweep + MACD, ICT Kill Zone + ATR, Adaptive RSI + OB, Multi-Factor Ensemble, Regime-Adaptive Trend, and more.

### Multi-Timeframe (5 strategies)
MTF Trend Align, MTF RSI Divergence, MTF Breakout Cascade, MTF Volatility Regime, MTF Structure Sync.

### Backtesting

```bash
# Run backtest on XAUUSD H1
python -c "
from dualbrain.strategy_lab import load_mt5_data, backtest_all
data = load_mt5_data('XAUUSD', 'H1', 5000)
results = backtest_all(data)
for name, score in results.ranking[:5]:
    print(f'{name}: {score:.2f}')
"

# Optimize parameters
python -c "
from dualbrain.param_optimizer import optimize_all
report = optimize_all('XAUUSD', 'H1')
print(report)
"

# Daily research cycle (backtest + optimize + report)
python dualbrain/research_scheduler.py
```

---

## 🔔 Telegram Alerts

Real-time notifications via QwenPaw's channel system:

| Alert Type | Trigger |
|------------|---------|
| 🟢 `TRADE_OPENED` | Position opened on MT5 |
| 🔴 `TRADE_CLOSED` | Position closed |
| 📊 `SIGNAL_GENERATED` | Every signal (even HOLD) |
| ⚠️ `DRAWDOWN_WARNING` | Drawdown > 8% |
| 🚨 `DRAWDOWN_CRITICAL` | Drawdown > 15% |
| 📅 `ECONOMIC_EVENT` | High-impact event imminent |
| 🔬 `RESEARCH_UPDATE` | New strategy found |

### Rate Limiting
- Minimum 1 second between alerts
- Deduplication: same alert type suppressed for 5 minutes
- Non-blocking: alerts don't halt the trading cycle

---

## 🧪 Testing

### Offline Tests (No LLM Required)

```bash
python dualbrain/test_offline.py
# 64 tests covering all infrastructure
```

**Tests include:**
- Config validation
- ToolBox permissions + dispatch
- TripleMemory write/read/search
- SignalEngine analysis
- Market hours detection
- Trade approval (heuristic)
- Strategy class loading
- Orchestrator instantiation
- DreamEngine processing
- LLMClient configuration

### Live Smoke Test (Requires LLM Proxy)

```bash
python dualbrain/test_smoke.py
```

### Full Integration Test

```bash
python dualbrain/test_integration.py
```

---

## 🚀 Deployment

### As a Windows Service (via QwenPaw Cron)

```bash
# Register the autonomous trader as a cron job
qwenpaw cron create \
  --name "autonomous-trader" \
  --schedule "*/30 * * * *" \
  --command "python dualbrain/autonomous_trader.py --once" \
  --agent-id evilagent
```

### As a Background Process

```bash
# Start the autonomous loop
start /B python dualbrain/autonomous_trader.py --loop --interval 1800 --log-level INFO
```

### Monitoring

```bash
# Check logs
tail -f autonomous_trader.log

# Check state
cat autonomous_trader_state.json | python -m json.tool

# Check memory
python dualbrain/main.py --memory
```

---

## ⚠️ Risk Warnings

**This system trades real money on a live MT5 account.**

- **Drawdown limit:** 15% — system auto-stops if exceeded
- **Risk per trade:** 2% of account balance
- **Max positions:** 3 simultaneous
- **Daily loss limit:** 5% of balance
- **All trades are logged** to TripleMemory for post-mortem analysis
- **Telegram alerts** fire on every trade and drawdown warning
- **Dialectical approval** adds a second AI opinion before execution

**Never deploy more capital than you can afford to lose.**

---

## 🛠️ Dependencies

### Required
```
httpx          # HTTP client for LLM + web APIs
```

### Optional (for full functionality)
```
MetaTrader5    # MT5 Python API (live trading)
numpy          # Strategy calculations
pandas         # Data manipulation
backtesting    # Strategy backtesting
playwright     # TradingView scraping
pyautogui      # Desktop automation
pyperclip      # Clipboard access
pygetwindow    # Window management
mss            # Desktop screenshots
```

---

## 📋 Configuration Reference

All settings in `dualbrain/config.py`:

| Setting | Default | Description |
|---------|---------|-------------|
| `LLM_BASE_URL` | `http://127.0.0.1:5200/v1` | OpenAI-compatible API endpoint |
| `THETA_MODEL` | `mimo-v2.5-free` | Explorer model |
| `EPSILON_MODEL` | `big-pickle` | Guardian model |
| `THETA_TEMPERATURE` | `0.8` | Explorer creativity (higher = more creative) |
| `EPSILON_TEMPERATURE` | `0.2` | Guardian skepticism (lower = more critical) |
| `MAX_DIALECTICAL_ROUNDS` | `2` | Debate cycles before forced synthesis |
| `MAX_EXECUTION_STEPS` | `15` | Max tool calls per execution phase |
| `CONVERGENCE_THRESHOLD` | `0.50` | Content-word overlap to consider converged |
| `EPISODIC_DIR` | `dualbrain/memory/episodic` | Interaction logs |
| `SEMANTIC_DIR` | `dualbrain/memory/semantic` | Patterns & insights |
| `PROCEDURAL_DIR` | `dualbrain/memory/procedural` | Gotchas & workflows |

---

## 🧬 Model Benchmarking

Models were benchmarked on 2026-07-15 across creative, analytical, and fast query types:

| Model | Speed | Output Quality | Reliability | Role |
|-------|-------|---------------|-------------|------|
| **mimo-v2.5-free** | 10-13s | ⭐⭐⭐⭐⭐ Richest output, most specific | 5/5 | Theta (Explorer) |
| **big-pickle** | 9-13s | ⭐⭐⭐⭐ Creative + analytical | 4/5 | Epsilon (Guardian) |
| nemotron-3-ultra-free | 3-8s | ⭐⭐⭐ Decent quality | 5/5 | Fallback |
| north-mini-code-free | 4-6s | ⭐⭐⭐ Fast, reasonable | 5/5 | Fallback |
| deepseek-v4-flash-free | — | ❌ 100% empty responses | 0/5 | Rejected |
| hy3-free | — | ❌ 100% empty responses | 0/5 | Rejected |

---

## 📜 License

MIT License — use freely, trade responsibly.

---

<div align="center">

**Built with ❤️ by Hadj**

*Two minds are better than one. Three layers of validation are better than two.*

</div>
