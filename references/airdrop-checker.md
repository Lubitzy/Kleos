# Airdrop Checker Strategy

Check NFT and token airdrop eligibility for **any wallet address** — Bankr wallet (auto-detected) or external wallets (MetaMask, Ledger, Phantom, etc.). Monitor community airdrops, and track claimed/unclaimed airdrops.

## Multi-Wallet Support

Kleos checks your **Bankr wallet** automatically. For external wallets, just provide the address:

```
"check airdrop eligibility for 0x1234..."
"check if 0xabcd... is eligible for [project] airdrop"
"add wallet 0x1234... to my airdrop tracker"
```

### Managing Wallets

```
"add wallet 0x1234... as 'Main ETH' to my tracker"
"add wallet solana:Abc... as 'Solana Vault'"
"show my tracked wallets"
"remove wallet 0x1234... from my tracker"
"check airdrops for ALL my wallets"
```

Tracked wallets are saved to `/.memory/nft-airdrops.md`:
```markdown
## Tracked Wallets
- Bankr (Base): 0xbankr... — auto
- Main ETH: 0x1234... — added: [date]
- Solana Vault: solana:Abc... — added: [date]
- Cold Storage: 0x5678... — added: [date]
```

### Batch External Wallet Check

```
"check airdrops for wallets: 0x1234..., 0x5678..., solana:Abc..."
"scan all my tracked wallets for new airdrops"
```

**Agent steps:**
1. For each wallet, use browser automation on claim pages
2. Most claim pages accept wallet address input directly
3. Present per-wallet eligibility summary
4. Flag which wallet needs to claim (user must do it manually from that wallet)

> ⚠️ Kleos can CHECK eligibility for external wallets, but can only CLAIM from the Bankr wallet. For external wallets, the user must claim manually using that wallet's interface.

## Understanding Airdrops

Airdrops are free token or NFT distributions to wallet holders. Common types:
- **Holder airdrops**: Rewards for holding a specific NFT or token at a snapshot date
- **Community airdrops**: Rewards for community participation (Discord, Twitter engagement)
- **Protocol airdrops**: Rewards for using a DeFi protocol (trading, providing liquidity)
- **Staking airdrops**: Rewards for staking tokens

Bankr does not have a native "check airdrop" tool. Use **browser automation** to check eligibility on official airdrop claim sites.

## Checking Airdrop Eligibility

### For a Specific Project

```
"check if I'm eligible for the [project] airdrop"
"am I eligible for [token] airdrop?"
"check if 0x1234... is eligible for [project]"
"check [project] eligibility for all my tracked wallets"
```

**Agent steps:**
1. Determine which wallet(s) to check — user's Bankr wallet (default) or provided address(es)
2. Ask the user for the official airdrop claim URL (or search for "[project] airdrop claim" using browser)
3. Navigate to the claim page using browser automation
4. If the page requires wallet connection, instruct the user: "Connect your wallet at [URL] to check eligibility. Bankr cannot connect to external dApps directly."
5. If the page accepts a wallet address input:
   - For Bankr wallet: get the address (`"what's my address on [chain]?"`)
   - For external wallets: use the address the user provided
   - Enter the address(es) on the claim page
   - Read and report results
6. Report: eligible amount, claim deadline, any conditions, which wallet is eligible

### Check Known Airdrop Platforms

Common airdrop platforms to check:

| Platform | URL | What to Check |
|----------|-----|---------------|
| Drops Tab (OpenSea) | opensea.io/drops | NFT airdrops and free mints |
| Earnifi | earnifi.com | Protocol airdrops by wallet |
| Degen Airdrops | Various | Community token airdrops |
| Project-specific pages | Varies | Official claim pages |

### Batch Eligibility Check

```
Prompt: "check my airdrop eligibility across [list of projects]"
```

**Agent steps:**
1. For each project, ask for or search for the claim URL
2. Check each one sequentially
3. Present a summary table:

```
🎁 Airdrop Eligibility Summary
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ [Project A]: 500 TOKEN — Claim at [URL] — Deadline: [Date]
✅ [Project B]: 0.1 ETH worth — Auto-claimed
❌ [Project C]: Not eligible (missed snapshot)
⏳ [Project D]: Claim page not live yet — Check back [Date]
```

## Community Airdrop Monitoring

### Track Upcoming Airdrops

```
Prompt: "what airdrops are coming up?"
Prompt: "monitor new airdrop announcements"
```

**Agent steps:**
1. Use browser automation to check airdrop aggregators, crypto news sites, and Twitter
2. Common sources:
   - OpenSea Drops page for NFT airdrops/mints
   - Major DeFi protocol blogs/announcements
   - Crypto Twitter (search for "airdrop announcement")
3. Present findings with: project name, eligibility criteria, snapshot date (if known), claim date
4. Save promising ones to `/.memory/nft-airdrops.md`

### Save to Airdrop Tracker

After finding an airdrop, save to `/.memory/nft-airdrops.md`:

```markdown
## Tracking
### [Project Name]
- **Type**: [Token/NFT]
- **Chain**: [base/ethereum/polygon/etc.]
- **Eligibility**: [Holder/Community/Protocol/Staking]
- **Snapshot**: [Date or "TBD"]
- **Claim**: [Date or "TBD"]
- **Claim URL**: [URL if known]
- **Status**: [Tracking/Claimed/Missed]
- **Amount Received**: [if claimed]
- **Notes**: [Any additional info]
```

### Set Up Monitoring Automation

```
Prompt: "alert me when [project] airdrop is claimable"
Prompt: "monitor [project] for airdrop claim opening"
```

Using Bankr automations:
```
"every day at 10am, check [claim URL] and alert me if the airdrop claim is live"
```

## Claiming Airdrops

### Manual Claim Guidance

Most airdrops require connecting a wallet to a dApp — which Bankr's terminal cannot do directly. Guide the user:

1. Go to the claim URL in their own browser
2. Connect the wallet that holds the eligible assets
3. Claim the airdrop

If Bankr's wallet holds the eligible assets, the user may need to:
- Export the private key (NOT recommended for shared/social wallets)
- Or transfer the eligible NFT/token to a wallet they control, then claim

### Track Claim Status

```
Prompt: "show my claimed and unclaimed airdrops"
```

Read from `/.memory/nft-airdrops.md` and present:
```
✅ Claimed: 3 airdrops (Total value: ~[X] ETH)
⏳ Pending: 2 airdrops (Claim not live yet)
❌ Missed: 1 airdrop (Deadline passed)
```

### Auto-Claim Detection

Some airdrops are auto-claimed (tokens appear in wallet automatically). When checking balances:

```
Prompt: "did I receive any new airdrops?"
```

**Agent steps:**
1. Check recent wallet activity: look for unexpected token/NFT transfers
2. Compare against known tracked airdrops in `/.memory/nft-airdrops.md`
3. For unknown incoming tokens: investigate (might be spam — warn user)
4. Log any found airdrops to the tracker

## Airdrop Safety & Scam Prevention

### Red Flags — Warn the User

- **"Connect your wallet to claim"** from unsolicited DMs or random sites
- **Asking for seed phrase or private key** — NEVER share these
- **Unfamiliar token in wallet** that requires visiting a site to "claim" or "unlock"
- **Claim sites that request unlimited token approvals**
- **Airdrops requiring a "claim fee"** — legitimate airdrops don't charge upfront
- **Social media accounts with few followers** claiming to be official

### Verify Before Claiming
1. Check the official project Twitter/Discord for the real claim link
2. Verify the URL domain matches the project's official domain
3. Never use links from DMs or random social media comments
4. Use a separate "burner" wallet for claiming unknown airdrops

### Dust Attack Awareness

If unknown NFTs appear in the wallet:
- Do NOT interact with them (no transfer, no list, no sell)
- They may be spam/scam NFTs designed to phish users who interact
- Warn the user: "Unknown NFT detected in your wallet. This may be a spam/scam. Do not interact with it on external sites."

## NFT Whitelist Checking

### Check Whitelist Status

```
Prompt: "check if I'm on the whitelist for [collection] mint"
```

**Agent steps:**
1. Ask user for the whitelist check URL (typically from the project's website or Discord)
2. Use browser automation to navigate to the check page
3. Enter the user's wallet address
4. Report whitelist status, mint allocation, and mint window

## Community Airdrop Phase Checking

For community airdrops with multiple phases (e.g., "Phase 1: Early Users, Phase 2: Holders"):

```
"check which airdrop phases I'm eligible for in [project]"
"check [project] phases for all my tracked wallets"
```

**Agent steps:**
1. Get project's airdrop phases documentation
2. For each wallet, for each phase, check criteria:
   - Phase 1 (Early Users): Check if wallet interacted with protocol before date X
   - Phase 2 (Holders): Check if wallet held token/NFT at snapshot
   - Phase 3 (Community): Check Discord/Twitter engagement (may need manual verification)
3. Present phase-by-phase eligibility per wallet:

```
🎁 [Project] Phases — Wallet: Main ETH (0x1234...)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ Phase 1 (Early Users): 200 TOKEN
✅ Phase 2 (Holders): 300 TOKEN
❌ Phase 3 (Community): Not eligible
Total: 500 TOKEN

🎁 [Project] Phases — Wallet: Bankr (0xbankr...)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
❌ Phase 1 (Early Users): No activity before snapshot
❌ Phase 2 (Holders): No tokens held
❌ Phase 3 (Community): Not eligible
Total: 0 TOKEN — wallet not eligible
```

## Airdrop Value Tracking

### Estimate Portfolio Value Including Airdrops

```
Prompt: "what's my total portfolio including unclaimed airdrops?"
```

Include pending airdrop values as "Unclaimed" in portfolio summary.

### Historical Airdrop Value

```
Prompt: "how much have I made from airdrops total?"
```

Sum claimed airdrop values from `/.memory/nft-airdrops.md`.

## Edge Cases

- **Claim page doesn't load**: The site might be overloaded during high-demand claims. Suggest trying at off-peak hours.
- **"Already claimed" error**: Check transaction history to confirm. Might be a different wallet claimed it.
- **Multi-wallet user**: If user has multiple wallets, ask which address to check.
- **Geoblocked claims**: Some airdrops restrict by country. Warn user if detected.
- **Expired claims**: Note the deadline in the tracker. Set a reminder automation 48h before deadline.