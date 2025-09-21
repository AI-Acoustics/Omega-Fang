# Omega-Fang
 Code Base Overview

  - omega-fang-crypto/ is the working repo: a Node.js Express API (crypto_backend_server.js) that fronts crypto/equity price data. It loads deterministic symbol “atlases” (coin_atlas.json, equity_atlas.json)
  for metadata, applies security middleware, memoizes provider calls (Coinbase, CoinGecko), exposes REST endpoints (/api/price, /api/candles, /api/stocks/*, /api/metrics, /health), and tracks request metrics/
  backoffs.
  - Front-end artifacts live alongside the API: dashboard.html and crypto_dashboard.html implement lightweight dashboards; static assets are served directly from Express. The UI is still vanilla HTML/JS, with
  React migration planned per docs.
  OpenAPI/AsyncAPI specs for Execution and Risk services validated via npm scripts (lint:openapi, lint:asyncapi) and CI.
  - Node dependencies are minimal (Express, Helmet, rate limiting, fetch polyfill). Dev tooling now includes Redocly CLI for OpenAPI validation; AsyncAPI CLI is bootstrapped via npx inside the lint script to
  keep dependencies lean.
  - Root-level extras: guardian.js for compliance logging hooks, atlas_policy.md documenting risk limits, various CSV/DB artifacts for analytics, and placeholder .logs/ excluded from Git. omega_fang/ currently
  just stores the high-level dev request.
