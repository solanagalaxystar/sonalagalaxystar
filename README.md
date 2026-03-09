# 🌌 Solana Galaxy

> An interactive solar system that maps the entire Solana ecosystem in real time — planets, wallets, whales, bridges and battles, all in one single-file web app.

![Solana Galaxy](https://img.shields.io/badge/Solana-Mainnet-14F195?style=flat-square&logo=solana&logoColor=white)
![Helius](https://img.shields.io/badge/Helius-API-9945FF?style=flat-square)
![Vanilla JS](https://img.shields.io/badge/Vanilla-JS-FFB800?style=flat-square&logo=javascript&logoColor=black)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero-14F195?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-white?style=flat-square)

---

## ✨ What is Solana Galaxy?

Solana Galaxy turns the entire Solana blockchain ecosystem into a living, breathing solar system you can explore in your browser. Solana is the sun. Each major sector — DeFi, Memes, NFTs, Gaming, RWA, Infrastructure — is a planet with orbiting satellites showing live metrics. Connect your Phantom wallet and watch your personal galaxy come to life.

No frameworks. No build step. One `.html` file.

---

## 🚀 Features

### 🌍 3D Solar System
- Solana as the animated central sun with corona, rays and pulse effects
- **10 ecosystem planets** orbiting at different speeds and distances
- Each planet has orbiting **metric satellites** (TVL, volume, users)
- Interactive **side panel** with protocols, links and real data on click
- Drag to pan · Scroll to zoom · Pinch on mobile

### ⚡ Live Data
- Real-time **TPS, slot, SOL price, TVL** via Helius RPC
- Updates every 3–15 seconds depending on metric
- **Heatmap mode** — planets glow green/red based on 24h performance
- **Liquidity flow lines** — animated routes between DeFi protocols

### 🚀 Wallet Connect (Phantom)
- Connect your Phantom wallet with one click
- **Interstellar Wallet Experience** — a cinematic journey through your on-chain identity
- Real data via Helius: transactions, tokens, NFTs, SOL balance
- Personalized **investor profile** (Whale, Strategic Trader, Memecoin Explorer, DeFi Architect…)
- **Galaxy Portfolio** — your assets visualized as planets
- **Replay Journey** — travel through your transaction history

### 🔥 Meme Radar
- Top 10 Solana memecoins ranked by market cap (CoinGecko data)
- Price, mcap, 24h volume, ATH and tags for each token
- Direct links to CoinGecko, Jupiter and Birdeye
- Slide-in panel on mobile, sidebar on desktop

### ⚔ Chain Wars
- **Battle Arena** — animated canvas with Solana vs Ethereum liquidity flow
- Green particles = capital flowing IN to Solana · Red = flowing OUT
- **TVL Scoreboard** — 6 chains ranked live (ETH, SOL, ARB, BNB, BASE, AVAX)
- **12 comparative metrics** — TPS, fees, developers, finality, uptime and more
- **Bridge flow feed** — Wormhole, deBridge, Allbridge, Circle CCTP and more
- Real-time feed of simulated cross-chain transactions

### 🔍 SF Tracker (Arkham-style)
- Monitors **8 Solana Foundation wallets** on-chain
- Arkham-style **node graph** — center wallet connected to 10 known entities
- Color-coded flow lines with particles and arrowheads
- **Live feed** with real transaction links to Solscan
- Add any custom wallet address to monitor
- Alerts for large movements

### 🐋 Whale Tracker
- Real-time feed of large on-chain movements (≥ $50K)
- Pulls actual transactions from monitored wallets via Helius
- **🐋 GIANT** badge for movements > $1M
- **REAL** badge on verified on-chain transactions
- Every transaction has a **↗ Ver TX** button linking directly to Solscan
- Click any transaction to open full detail panel with Solscan, Explorer and Birdeye links

### ⌨ Dev Mode
| Tool | Description |
|------|-------------|
| 🐋 Whale Tracker | Live feed of large on-chain movements |
| 🔍 TX Debugger | Paste any Solana transaction hash and inspect it |
| ⚡ RPC Playground | 16 Solana RPC methods with live JSON responses |

### 🌐 Multilingual
- Full **PT 🇧🇷 / EN 🇺🇸** support
- One-click toggle in the navbar
- All sections translated including Chain Wars, Dev Mode and Meme Radar

---

## 🛠 Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML5 / CSS3 / JavaScript |
| Rendering | Canvas 2D API (dual canvas — starfield + main) |
| Data | Helius API · Solana RPC · CoinGecko |
| Wallet | Phantom Wallet SDK (window.solana) |
| Hosting | Any static host or Node.js server |

**Zero npm packages in the frontend. No React. No bundler. No build step.**

---

## 📦 Project Structure

```
solana-galaxy/
├── index.html              # Entire frontend — one file (~250KB)
└── server/                 # Optional Node.js proxy (keeps API key secure)
    ├── server.js           # Express proxy server
    ├── package.json
    ├── vercel.json         # One-click Vercel deploy config
    ├── .env.example        # Environment variables template
    └── public/
        └── index.html      # Copy of the frontend served by the proxy
```

---

## ⚡ Quick Start

### Option 1 — Open directly in browser (demo mode)
```bash
git clone https://github.com/your-username/solana-galaxy.git
cd solana-galaxy
open index.html
```

Works immediately. Wallet connect and Whale Tracker will run in demo mode without a Helius key.

---

### Option 2 — Full real-time data (recommended)

#### 1. Get a free Helius API key
Create one at **[dev.helius.xyz](https://dev.helius.xyz)** — the free plan gives 100,000 requests/month.

#### 2. Run the proxy server
```bash
cd server
npm install
cp .env.example .env
```

Edit `.env`:
```env
HELIUS_API_KEY=your_key_here
PORT=3000
```

```bash
node server.js
```

Open **http://localhost:3000** — all features enabled, API key never exposed to the browser.

---

### Option 3 — Deploy to Vercel (free, public URL)
```bash
cd server
npm install -g vercel
vercel login
vercel
vercel env add HELIUS_API_KEY   # paste your key when prompted
vercel --prod
```

Your app will be live at `https://your-project.vercel.app` — anyone can access it without needing their own API key.

---

## 🔒 Security

The proxy server pattern means:

```
User browser  →  /api/wallet/ADDRESS  →  Your server (Helius key stored here)  →  Helius API
                        ↑                                                               ↓
              No API key in the browser                                        Real on-chain data
```

- Your Helius key is **never sent to the browser**
- Rate limited to **60 requests/minute per IP** to protect your quota
- Wallet connect only reads the **public address** — never private keys or signing

---

## 🌐 Wallet Data (when connected)

When a user connects their Phantom wallet, the app fetches via Helius:

| Data | Source |
|------|--------|
| Transaction history (last 100) | Helius Enhanced Transactions API |
| SPL token balances | Solana RPC `getTokenAccountsByOwner` |
| NFT collection | Helius DAS API `getAssetsByOwner` |
| SOL balance | Solana RPC `getBalance` |
| Investor profile | Calculated on-chain (DeFi/meme/NFT activity) |

---

## 📊 Data Sources

| Source | Used for |
|--------|---------|
| [Helius](https://helius.dev) | RPC, wallet data, transactions, NFTs |
| [CoinGecko](https://coingecko.com) | Meme coin prices and rankings |
| [DefiLlama](https://defillama.com) | TVL data for all chains and protocols |
| [Solana RPC](https://solana.com) | TPS, slot, validators |
| [Birdeye](https://birdeye.so) | Token links and portfolio |
| [Wormhole](https://wormhole.com) | Bridge flow data |
| [deBridge](https://debridge.finance) | Cross-chain transfer data |

---

## 🤝 Contributing

Pull requests are welcome. For major changes please open an issue first.

```bash
git clone https://github.com/your-username/solana-galaxy.git
cd solana-galaxy
# Edit index.html — that's it
```

---

## 📄 License

MIT — use it, fork it, build on it.

---

<div align="center">

Built with ❤️ for the Solana ecosystem

**[⭐ Star this repo](https://github.com/your-username/solana-galaxy)** if you find it useful

</div>
