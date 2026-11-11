# ATS GOLD BOT — Android PWA prototype

## What this is
An installable Android web app (PWA) prototype. It is not an APK and is not yet a native Play Store app. Host the folder on an HTTPS static host, open the URL in Chrome on Android, then use Chrome menu → Install app / Add to Home screen.

## Data
Uses the independent XAUS API:
- `https://xaus.com/api/v1/intraday?symbol=xau&hours=48`
- Observations are sampled about every 5 minutes.
- The app aggregates samples into indicative 5m, 15m and 1h buckets.
- XAUS prices are indicative mid-market references, not XNance executable quotes.
- Feed outages or old observations cause WAIT/no signal.

## Signal rules
- EMA 20/40 direction on M5, M15 and H1 must agree.
- M5 close must be on the trend side of EMA20.
- M5 RSI14: 55–70 for BUY; 30–45 for SELL.
- Suggested stop distance = 2 × M5 ATR14; TP1 = 1R; TP2 = 2R.
- These are unvalidated prototype rules, not a tested profitable strategy or an ML prediction model.

## Limitations / next development
- The feed provides sparse sampled spot observations, not tick data or a broker bid/ask feed.
- Aggregated bars are indicative approximations, not exchange/broker OHLC candles.
- Browser notifications work only when supported and permission is granted; reliable background alerts may require a backend/push service.
- No trade execution, broker login, account access, or order placement exists in this project.
- Backtest, forward-demo test, data-quality review, and user testing are required before relying on signals.
