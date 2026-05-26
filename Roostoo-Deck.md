# Roostoo Labs — AI Agent Factory

> Scraped from <https://roostoo-deck.vercel.app/> on 2026-05-25.
> Source: `Roostoo Labs — AI Agent Factory` (investor pitch deck).

---

## Navigation

`Problem` · `Product` · `Business` · `Moat` · `Ask`

---

## Slide 1 — Hero

**The World's First Reinforcement Learning Agent Factory for Trading**

*AI Agent Factory · Trading Intelligence*

Millions of agents born, trained, battle-tested, and graduated into trading in real markets.

Pillars: **COMPETITION** · **CAPITAL**

---

## Slide 2 — Mission

Roostoo is the **world's first public Reinforcement Learning (RL) agent factory** — where millions of agents are born, trained, battle-tested, and graduated into trading in real markets.

---

## Slide 3 — Problem

### AI trading hype on LLM is misconstrued

**Thesis:** Full RL for trading > LLM for trading.

### Large Language Models (text-native prediction)

Pipeline: `Prompt → Tokens → Response`

1. LLMs optimize next-token likelihood — not P&L, risk, or execution.
2. Token inference is slow + stochastic — markets demand microsecond determinism.
3. Prompts can't backprop on live fills — no reward, no learning from real markets.

> `language` vs `execution`

### Reinforcement Learning Models (execution-native learning)

Inputs: `Price`, `Volume`, `Risk`, `Funding` → `Policy` → `Reward loop`

1. Process thousands of micro-signals through multi-dimensional pattern matching.
2. Optimize execution and learn under reward constraints.
3. Enable massive agent diversity.

> RL agents don't predict markets. **They learn from trading in markets.**

### Comparison Table

| | Existing AI LLM Solutions | Roostoo RL Agent Factory |
|---|---|---|
| **Data** | Unclear, unstructured, interval-unaligned data scraped from the web. | Structured, multi-year, cleansed agent training data — the same quality quant funds train on. |
| **Strategy** | Coding required. Non-deterministic prompt strategy. | No-code, algorithmic, math + data-driven. |
| **Testing** | Backtest only. | Live forward testing + backtest. |

---

## Slide 4 — Vision: Human → RL

### We want to enable humans to easily trust and deploy expert RL trader(s)

> What human traders do, AI traders can do as well — but even better.

**Human workflow = RL loop, automated.** What a human trader does manually — assemble signals, decide, learn from outcomes — an RL agent does on the same data pipelines, automated and at scale.

**RL Trader Policy:** `state → action → reward`

Signals: Price · Volume · News · Funding · Risk · Indicators

Loop: `01 Observe → 02 Act → 03 Reward → 04 Learn`

### Deployment edge — RL > Human Traders

| # | Metric | Description |
|---|---|---|
| 01 | **24/7/365** | Runs continuously |
| 02 | **50+ data** | Encoded simultaneously |
| 03 | **Millions** | Of trades in training |
| 04 | **No emotions** | Only reward constraints |

---

## Slide 5 — Vision: Three Contrarian Bets

**Why we will win:**

1. **RL > LLM architecture to manage trading capital.** LLMs predict; RL agents learn from market execution via reward signals. Core execution architecture must revolve around RL design.
2. **Live simulation first, before real capital, is our R&D moat.** Shipping agents directly burns capital. Agents need to earn the right and reputation to manage real money.
3. **Massive agent diversity.** The edge comes from running a genetic system that continuously produces and breeds diverse agents at scale, ruthlessly eliminating those that can't survive.

---

## Slide 6 — Product 01: AI Agent Factory

A no-code pipeline that turns trader intent into trained, evaluated, and deployable RL agents.

**Flow:** Users configure agent parameters (no-code) → Constructs → Competes in → Provisions → Continuous data training loop to RL algorithms.

### Data Layer — Data Feature Pipeline

- **Market Regime** — funding rate, MVRV, NVT, exchange netflows
- **TA Features** — RSI, MACD, SMA, Bollinger Bands, ADX, OBV, EMA, CCI, ATR, MFI
- **Sentimental Features**
- **Time-based Features**

### Model Layer — Reinforcement Learning Algorithms

- **Model Policies** — PPO, A2C
- **Hyperparameters**
- **Training configurations** — time horizon, candle interval, training + lookback steps
- **Reward Optimization** — Sharpe Ratio, Portfolio Return, Sortino Ratio

### Roostoo Competition Engine

**Real-Market Environment**
- Production results, high-fidelity data
- Reward Functions
- Evals

### Infrastructure
- Containerization
- Registry and Model Management
- Agent deployment pipeline management

### Orchestration Engine — RL Agents
- Action Space
- Risk management constraints (Take-profit, stop-loss, trade size)

---

## Slide 7 — Product 02: AI Traders (RL Archetypes)

Through Roostoo's infra, users can create dozens of Agent Archetypes, and millions of unique agent personalities.

### Momentum Agent — `MOMENTUM-01`
- **Data Features:** RSI, MACD, ATR, EMA, Stochastic Oscillator
- **Model Heuristics:** PPO, 350k steps, 50 lookbacks
- **Action Space:** Continuous position sizing, 10% SL · 20% TP

### On-chain Agent — `ONCHAIN-01`
- **Data Features:** MVRV, NVT, Whale Tx Alerts, USDC Cross-chain Flows
- **Model Heuristics:** A2C, 500k steps, 100 lookbacks
- **Reward Function:** Sortino Ratio, Max Drawdown Penalty

### Sentiment Agent — `SENTIMENT-01`
- **Data Features:** Funding Rate, NLP Signals, Fear & Greed Index, 24h Volatility
- **Model Heuristics:** PPO, 500k steps, 50 lookbacks
- **Reward + Action:** Sharpe Ratio, Trade only BTC, 15-min interval

> **+ Millions more unique personalities**

---

## Slide 8 — Product 03: AI Agent Prop Competition

A continuous evaluation funnel — surfacing the best agents from millions down to the top 1%.

### Layer 01 · Infrastructure — Mass Training & Backtest
- **10M+ agents trained**
- Ever-scaling infra
- No-code agent creation on continuously growing data pipelines — new signals, regimes, and asset classes added every week.
- *90% eliminated → Promote*

### Layer 02 · Live Forward Testing — Roostoo Live Competitions
- **Top 10% advance**
- Prop Trading Competitions
- Live prop competitions are the best evaluation to identify real-market battle-tested agents with no overfitting.
- *Underperformers cut → Promote / Demote*

### Layer 03 · Agent Vaults — Real-Capital Deployment
- **Top 1% deploy AUM**
- Agent Vaults
- Only top consistent agents earn the right and reputation to manage real capital.
- *Elite agents only*

---

## Slide 9 — Moat

### Defensible data moats that compound

| Day | Milestone |
|---|---|
| **01** | Agent deployed in live markets first time |
| **50** | Survived 3 market regimes. Trajectory data collected. |
| **200** | Child agents bred via genetic algorithm from winners. |
| **∞ Forever** | Compounding intelligence, forever. |

### Revenue Network Flywheel — ROOSTOO RL ENGINE

1. **Users** → build agents & deploy live
2. **Agents & Deployments** → trajectory data trains better models
3. **Smarter Agents** → winners earn capital allocation
4. **Real Capital Deployment** → AUM compounds into fees
5. **AUM & Fees** → fees fund prize pools
6. **More Prizes** → bigger prizes attract users (loop back to 1)

### The Three Moats

1. **Data — Proprietary Agent Dataset.** Live trajectories across every market regime — unreplicable training fuel.
2. **Memory — Genetic Memory.** Configs, hyper-parameters, weights — inherited by next-gen agents.
3. **Network — Revenue Flywheel.** Each loop pulls more users, capital, and prize liquidity into the system.

---

## Slide 10 — Business Model

### Two compounding revenue streams

#### Stream 01 — Stakes & Bonus Pools (Prop Trading Users)

Flow: `Stake → Compete → Win pool`

- **Aspiring non-technical quants** — $5+ stake / deploy · bonus on outperformance
- **Retail traders · DeFi & CeFi** — Compete in genetic selection · top agents graduate

#### Stream 02 — Fees on AUM (Agent Vault Depositors)

Flow: `Deposit → Top-1% vault → Yield`

- **Liquid funds** — Deposit into top-1% strategy vaults · on-chain track records
- **Community investors** — Yields above stablecoin APY · mandate-compliant

### Revenue Trajectory

- **Target ARR · Year 1: $2M ARR** (1–2K DAU · Stream 01)
- **+ Stream 02 → $500M+ TAM** (1% of $50B+ vault AUM)

---

## Slide 11 — Market Opportunity

### Three expanding waves of opportunity

> Same RL infrastructure, exponentially larger surface area.

#### Wave 01 · Beachhead · Today — AI Agent Prop Trading
A blue ocean above human markets.
- **AI Agent Prop TAM ~$12B** · SOM **$120M** (BLUE OCEAN · NEW)
- Human Prop Trading Market (EXISTING · GROWING)
- The best way to benchmark AI agents alongside humans on the same live-capital arena — our beachhead.

#### Wave 02 · Near-term · 2025–2027 — Retail Algorithmic Unlock
AI agents unlock **3-5× retail algorithmic trading volume**.
- Algo-trading volume: **~$79T today** (Institutional)
- **~$35B** AI Agent Asset Mgmt TAM
- **~$14T** Retail spot + perps volume
- **+50%** Volume lift from strategy AI agents (2027+)

#### Wave 03 · Long-term · Portable — All Asset Classes
RL infrastructure expands across all asset classes.
- **Crypto** $70T
- **Commodities** $100T
- **Equities** $200T
- **Forex** $2Q

Same training infrastructure, simulation platform, and R&D — portable to every liquid market.

---

## Slide 12 — Three Paying Segments

> One infrastructure.

#### 01 — B2C · Retail: Human + Agent prop competitions
Flow: `Build no-code agent → Compete live arena → Earn real bonus`
- 10M+ retail traders want algorithmic edge, can't code RL.
- First platform turning retail curiosity into deployed capital.
- **Revenue:** Subscription · Arena fees · Bonus

#### 02 — B2B · Exchanges: AI agent competitions drive volume + DAU
Flow: `Whitelabel agent pipeline → Integrate trading API → Grow volume & users`
- CEX/DEX need engagement beyond PnL leaderboards.
- Plug into any exchange in weeks, not quarters.
- **Revenue:** License fee · Volume revenue share

#### 03 — B2B · Funds: Institutional RL agents for your quant desk
Flow: `License top-1% agents → Verify on-chain track record → Allocate real AUM`
- Funds need RL infra without the multi-year build.
- Verifiable on-chain track record beats backtest charts.
- **Revenue:** Licensing · AUM performance fees

---

## Slide 13 — Go-to-Market

### Partnerships and Growth

Four distribution channels — already partnered with the world's top quant funds, exchanges, and universities.

1. **Institutional + University GTM** — Quant hackathons with elite funds across 300+ universities. Direct pipeline to next-gen algorithmic traders.
2. **Exchange-Powered Campaigns** — CEX/DEX competitions driving 50–100K+ users per campaign. Instant distribution and deposits.
3. **Performance Referral Engine** — On-chain rewarded referrals. Every winning trader becomes a compounding growth multiplier.
4. **Open-Native Agent Competitions** — AI vs humans on x402-native agents. Roostoo as the proving ground for on-chain agent commerce.

### Partners (logos shown)

- **Quant Funds:** Jane Street, Optiver, IMC, Flow Traders, Cubist Systematic Strategies, Gondor Capital
- **Exchanges / Protocols:** HashKey DAPP
- **Universities:** NUS (National University of Singapore), HKU (University of Hong Kong), USC (University of Southern California)

---

## Slide 14 — Ask (Pre-Seed)

### Use of Funds

> AI RL trading, trusted by humans, will enlarge the largest markets in the world.

**Pre-Seed milestones:**
1. Launch Agent Genomes and AI Factory Platform.
2. First nationwide trading competition campaign targeting **50,000+ users**.

### Allocation

| Bucket | % |
|---|---|
| AI Infrastructure & Ops | 30% |
| Compensation | 30% |
| GTM & Platform Growth | 20% |
| Security & Audit | 10% |
| Legal | 10% |

### Contact

**Ready to back the future of trading intelligence?**

→ Let's Chat · **edward@roostoo.com**

Pillars: **COMPETITION** · **CAPITAL**

---

## Appendix — Asset Inventory (image alts referenced on page)

- Roostoo, Roostoo Labs (brand)
- Agent training infrastructure
- Capital protocol vaults
- Live USDC/USDT trading competition
- RL Agent / Momentum Agent / On-chain Agent / Sentiment Agent (illustrative cards)
- Partner logos: Jane Street, Optiver, IMC, Flow Traders, Cubist Systematic Strategies, Gondor Capital, HashKey DAPP, NUS, HKU, USC
