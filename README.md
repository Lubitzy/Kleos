# Kleos — NFT Agent for Bankr

<p align="center">
  <img src="assets/banner.svg" alt="Kleos — AI NFT Agent for Bankr" width="100%">
</p>

> *κλέος* — the Greek concept of eternal glory earned through heroic deeds.  
> **Kleos hunts NFT glory** — sweeping floors, sniping mints, managing portfolios, and claiming airdrops.

Kleos is a [Bankr](https://bankr.bot) skill that transforms your AI agent into a full-stack NFT trading machine. It works on Telegram, X (Twitter), and the Bankr web terminal — all through natural language.

---

## Features

| Module | What It Does |
|--------|-------------|
| **Floor Sweeper** | Buy cheapest NFTs from any collection — single or batch. Auto-list at profit targets. Stop-loss protection. Multi-collection sweep. |
| **Mint Sniper** | Discover upcoming NFT drops. Research collections before minting. Auto-mint when live. Post-mint floor monitoring. |
| **Portfolio Manager** | Track PnL per NFT & collection. Floor price alerts. Bulk listing/offer management. Portfolio rebalancing. Watchlist. |
| **Airdrop Checker** | Check eligibility for token & NFT airdrops. Monitor community airdrops. Phase-by-phase eligibility. Scam detection. Dust attack warnings. |
| **Batch Transfers** | Send multiple NFTs at once. Transfer to ENS, addresses, or Twitter handles. |

All activity is logged to persistent memory (`/.memory/nft-activity.md`) for long-term PnL tracking.

---

## Quick Install

In your Bankr agent ([bankr.bot](https://bankr.bot), [Telegram](https://t.me/bankr_ai_bot), or X):

```
install the skill at https://github.com/Lubitzy/kleos/tree/main
```

**That's it.** Kleos activates automatically whenever you talk about NFTs.

---

## Usage Examples

### Floor Sweeping
```
"kleos, sweep 3 floor Based Punks on base"
"buy the cheapest Noun and auto-list at 2x"
"set stop loss on my Pudgy Penguins — sell if floor drops 30%"
```

### Mint Sniping
```
"kleos, what's minting today?"
"monitor the Doodles mint and auto-mint 2 when it goes live"
"research this collection before I mint"
```

### Portfolio Management
```
"kleos, show my NFT portfolio"
"list all my Nouns at 10% above floor"
"accept all offers above 0.5 ETH on my NFTs"
"alert me if any collection in my portfolio pumps 50%"
```

### Airdrop Checking
```
"kleos, am I eligible for any airdrops?"
"check which airdrop phases I qualify for in Optimism"
"monitor new community airdrops and alert me"
```

---

## Automation Presets

Kleos comes with ready-to-use Bankr automation presets. See [`presets/`](presets/) for one-click setups:

| Preset | Command |
|--------|---------|
| Floor Monitor | `"every hour, check floor of [collection] and alert me if it moves >5%"` |
| Mint Watcher | `"every day at 9am, show me what's minting today"` |
| Portfolio Pulse | `"every 6 hours, show my NFT portfolio PnL"` |
| Airdrop Scout | `"every day at 10am, search for new airdrops and check my eligibility"` |

[→ View all presets](presets/)

---

## Memory System

Kleos saves state to your Bankr agent's persistent filesystem:

| File | Purpose |
|------|---------|
| `/.memory/nft-activity.md` | Timestamped log of all buys, sells, mints, transfers |
| `/.memory/nft-watchlist.md` | Collections you're monitoring |
| `/.memory/nft-airdrops.md` | Airdrops you're tracking or have claimed |
| `/.memory/nft-targets.md` | Profit targets and stop losses for holdings |

---

## Supported Chains

NFT operations are available on: **Base**, **Ethereum**, **Polygon**, **Unichain**

> Prefer **Base** — gas is sponsored by Bankr. Ethereum mainnet gas can exceed NFT value.

---

## Requirements

- A [Bankr](https://bankr.bot) account (free tier works, Bankr Club recommended for automations)
- NFT operations require sufficient ETH/WETH balance on the target chain

---

## Structure

```
kleos/
├── SKILL.md                    # Core skill instructions
├── assets/
│   └── banner.svg              # Repo banner
├── references/                 # Detailed workflow docs (loaded on demand)
│   ├── floor-sweeper.md        # Floor sweeping strategies
│   ├── mint-sniper.md          # Mint sniping workflows
│   ├── portfolio-manager.md    # Portfolio tracking & PnL
│   └── airdrop-checker.md      # Airdrop eligibility checking
├── presets/                    # Copy-paste automation commands
│   ├── sweeper.md
│   ├── sniper.md
│   ├── portfolio.md
│   └── airdrop.md
├── LICENSE                     # MIT
└── CONTRIBUTING.md             # Contribution guide
```

---

## License

MIT © 2026 Kleos — free to use, modify, and distribute.
