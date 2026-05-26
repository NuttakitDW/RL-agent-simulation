Plain English Explanation

  The Big Picture

  You're building a crypto trading bot that learns by trial and error (using PPO, the algorithm from the paper we just discussed). It trades
  15-17 coins at once on Roostoo/Binance/Hyperliquid. On top of the bot, you're adding a "glass box" UI so users can actually see what the bot
  is thinking — solving the classic "AI black box" complaint.

  ---
  Part 1: The Transparency Layer (Why this whole thing exists)
  
  People don't trust AI traders because they look like a black box: money goes in, trades come out, no one knows why. Your fix:

  - Signal Inputs — show users every piece of data the bot is looking at (RSI, MACD, volume, etc.) as "strength bars" in the UI.
  - Signal Output — show the bot's final decision as a strength bar too (e.g. "85% conviction to buy").
  - Why this matters — it gives RL agents the same "show your work" feel that LLMs get from chain-of-thought reasoning. The user can see the
  bot weigh evidence.

  ---
  Part 2: What the Bot Sees (Observation Space)
  
  Every 5 minutes, for each coin, the bot looks at a giant table of numbers:

  17 features × 50 past time periods × N coins

  The 17 features break down as:

  - 2 raw market signals: price change, volume change
  - 8 technical indicators: RSI, MACD, StochRSI, EMA crossover, VWAP, OBV, Bollinger bands, ATR (these are the standard charting tools traders
  use)
  - 4 time signals: hour, day, weekday, month (so it can learn "weekends are weird")
  - 3 portfolio signals: how much cash you have, how much of this coin you hold, are you up or down

  Key trick: every number is squeezed into the range -1 to +1 (using tanh or simple scaling). Neural nets hate raw numbers like "BTC = $67,432"
   — they prefer everything on the same small scale.

  Smart bit: the portfolio numbers (cash, position, PnL) are kept in a rolling 50-step history, so the bot doesn't just see "I own 0.5 BTC
  right now" — it sees "I've been holding 0.5 BTC and slowly losing money for 4 hours."

  ---
  Part 3: What the Bot Does (Action Space)

  For each coin, the bot outputs one number between -1 and +1:

  ┌──────────────┬─────────────────────────────────────────────────────┐
  │    Output    │                       Meaning                       │
  ├──────────────┼─────────────────────────────────────────────────────┤
  │ -1.0 to -0.1 │ Sell (the more negative, the more aggressive)       │
  ├──────────────┼─────────────────────────────────────────────────────┤
  │ -0.1 to +0.1 │ Hold (the "deadzone" — don't trade on weak signals) │
  ├──────────────┼─────────────────────────────────────────────────────┤
  │ +0.1 to +1.0 │ Buy (the more positive, the more aggressive)        │
  └──────────────┴─────────────────────────────────────────────────────┘

  The Exponential Curve Trick

  Instead of "0.5 conviction = 50% position", you reshape the signal with an exponential curve. This means:

  - Weak signals (0.3) get smaller positions than linear (~10% instead of 30%)
  - Strong signals (0.8) get bigger positions (~72%)
  - Maximum confidence still maps to 100%

  Why: punishes wishy-washy decisions, rewards decisive ones. You don't want a trader who half-commits to every guess.

  Position Sizing Rules

  When the bot says "buy", it doesn't just yolo. The actual dollar amount is capped by whichever is smallest of:
  - The signal-scaled budget (~$400 per step)
  - Max single trade ($1,250)
  - Available cash minus a $25 reserve
  - 60% portfolio cap per coin

  ---
  Part 4: The Safety Net (Risk Management)

  Even if the AI goes crazy, hard limits override it:

  ┌──────────────────────────────┬───────────────────────────────┐
  │            Guard             │         What happens          │
  ├──────────────────────────────┼───────────────────────────────┤
  │ Lost 15%?                    │ Dump everything, stop trading │
  ├──────────────────────────────┼───────────────────────────────┤
  │ Made 25%?                    │ Take profits, stop trading    │
  ├──────────────────────────────┼───────────────────────────────┤
  │ Down 20% from peak?          │ Dump everything, stop         │
  ├──────────────────────────────┼───────────────────────────────┤
  │ One coin > 60% of portfolio? │ Block further buys of it      │
  ├──────────────────────────────┼───────────────────────────────┤
  │ Less than $10 trade?         │ Skip it (fees would eat it)   │
  ├──────────────────────────────┼───────────────────────────────┤
  │ Leverage / shorting?         │ Disabled. Long-only, 1× only. │
  └──────────────────────────────┴───────────────────────────────┘

  This is the "agents must earn the right to manage real capital" line from your pitch deck made concrete.

  ---
  Part 5: The Pipeline (How One Step Works)

  Market data → Calculate indicators → Normalize to [-1,1] →
  Feed into PPO brain → Get action per coin → Apply sizing & risk caps →
  Execute trade → Update portfolio → Calculate reward →
  Send reward back to PPO so it learns

  The reward is: 0.5 × Sharpe ratio + 0.4 × profit − 0.05 × drawdown (clipped to ±10). Translation: the bot is rewarded for risk-adjusted
  profit, not just profit — and gets penalized for big swings down.

  ---
  Part 6: The User-Facing Product (Architecture)
  
  This is the "glass box" UI from Part 1, built as a Flask web app:

  1. User logs in → sees a dashboard with live trades streaming in
  2. Each trade is captured with full context (which indicators were firing, what the portfolio looked like, why it traded) and stored in
  SQLite
  3. A local LLM (DeepSeek-R1 8B running via Ollama) turns that raw data into plain-English explanations on demand
  4. Chat panel lets users ask "why did you buy ETH at 3pm?" and the LLM answers using the stored trade context

  Why a local LLM (Ollama, not OpenAI):
  - Zero cost per query
  - Runs on your RTX 5050
  - Trade data never leaves the machine
  Market data → Calculate indicators → Normalize to [-1,1] →
  Feed into PPO brain → Get action per coin → Apply sizing & risk caps →
  Execute trade → Update portfolio → Calculate reward →
  Send reward back to PPO so it learns

  The reward is: 0.5 × Sharpe ratio + 0.4 × profit − 0.05 × drawdown (clipped to ±10). Translation: the bot is rewarded for risk-adjusted
  profit, not just profit — and gets penalized for big swings down.

  ---
  Part 6: The User-Facing Product (Architecture)

  This is the "glass box" UI from Part 1, built as a Flask web app:

  1. User logs in → sees a dashboard with live trades streaming in
  2. Each trade is captured with full context (which indicators were firing, what the portfolio looked like, why it traded) and stored in
  SQLite
  3. A local LLM (DeepSeek-R1 8B running via Ollama) turns that raw data into plain-English explanations on demand
  4. Chat panel lets users ask "why did you buy ETH at 3pm?" and the LLM answers using the stored trade context

  Why a local LLM (Ollama, not OpenAI):
  - Zero cost per query
  - Runs on your RTX 5050
  - Trade data never leaves the machine
  - DeepSeek-R1 has good reasoning for "explain this decision" style prompts

  ---
  TL;DR

  You're building a transparent crypto RL trader. The PPO agent watches 17 normalized features across 50 time steps for 15+ coins, outputs a -1
   to +1 signal per coin, scales positions with an exponential curve, and has hard risk guards as safety nets. The differentiator vs every
  other trading bot is the UI + local LLM layer that turns each trade into a human-readable explanation — so users can finally trust what the
  AI is doing.