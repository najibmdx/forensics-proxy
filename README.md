# Forensics Proxy

API proxy for the Memecoin Forensics Analyzer. Routes calls to Helius, Arkham, and Currents News — bypassing browser CORS restrictions from the Claude artifact.

## Deploy to Vercel (5 minutes)

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → New Project → Import your repo
3. Click Deploy (no config needed — Vercel auto-detects the `api/` folder)
4. Copy your deployment URL (e.g. `https://forensics-proxy-abc123.vercel.app`)
5. Paste it into the artifact's PROXY_URL field

## Endpoint

`POST /api/proxy`

### Actions

**helius_rpc** — any Helius JSON-RPC call
```json
{ "action": "helius_rpc", "payload": { "method": "getAsset", "params": { "id": "TOKEN_MINT" } } }
```

**helius_tx** — Helius Enhanced TX API
```json
{ "action": "helius_tx", "payload": { "signature": "TX_SIG" } }
```

**arkham** — Arkham intelligence address lookup
```json
{ "action": "arkham", "payload": { "address": "WALLET_ADDRESS" } }
```

**currents_search** — Currents News API
```json
{ "action": "currents_search", "payload": { "keywords": "hantavirus", "limit": 10 } }
{ "action": "currents_search", "payload": { "category": "health", "limit": 20 } }
```
