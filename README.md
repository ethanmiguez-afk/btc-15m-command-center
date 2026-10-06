BTC 15M COMMAND CENTER — ULTRA-FAST

This build is READ-ONLY. It never places orders.

Fast architecture:
- Coinbase public WebSocket for real-time price/trades.
- Kraken public WebSocket for independent real-time price/trade confirmation.
- Kalshi market, order book, and recent-trades refresh loops run independently of BTC/ETH candle history.
- The model recomputes locally about every 250 ms between network updates.
- Browser polls only the compact local state, so UI updates do not wait for exchange HTTP requests.
- Closed 1-minute candles drive the core model; the current forming candle is displayed separately.

DECISION LOGIC
- BUY is stricter than “favored side”.
- Requires high estimated win probability, meaningful Kalshi edge, multi-timeframe alignment, component agreement, fresh feeds, acceptable entry price, and 12-second stability.
- WAIT explains the blockers.
- Once BUY is confirmed, the side is locked until TAKE PROFIT or EXIT.
- The dashboard displays BUY UP, BUY DOWN, WAIT FOR UP, WAIT FOR DOWN, and settlement win/loss odds.
- Suggested stake uses conservative capped fractional-Kelly sizing from the bankroll you enter.

RUN
1) Stop older server with Ctrl+C.
2) Extract into a new folder.
3) In Command Prompt inside that folder run: node server.js
4) Open the URL below.

URL: http://127.0.0.1:8787

IMPORTANT
- Probabilities are model estimates, not guarantees.
- Kalshi crypto markets settle from the contract's specified CF Benchmarks Real-Time Index; exchange feeds are not mislabeled as BRTI.
- To use the exact BRTI settlement feed and authenticated Kalshi WebSocket channels, add Kalshi API credentials separately; this build remains read-only.
