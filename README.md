# Language.fi Letter Explorer

The Language.fi Letter Explorer is a live market dashboard for the alphabet, showing each letter's price, usage, source breakdown, token popularity, weekly trend markets, and settlement proofs from the Language.fi Letter Usage Oracle.

## What This Is

A Bloomberg terminal for the alphabet, where every letter becomes a live market. Letters are tracked, priced, traded, and settled using the Language.fi Oracle, which measures live letter and number usage across Solana names, NFT collections, domains, registry entries, and Gate.io token listings.

## Letter Usage Oracle

### Oracle Sources (Clean Source Set)
- Solana token names
- Solana NFT collection names
- Solana domain names
- Language.fi registry entries
- Gate.io token listings

### What the Oracle Measures
For every supported character (A-Z, 0-9, SPACE, and allowed symbols), the oracle publishes:
- Unique items containing the character
- Total character occurrences
- Week-over-week change
- Source-by-source contribution
- Protocol rank
- Volatility
- Oracle confidence

### Source Weighting
To reduce manipulation risk from one noisy source, the oracle applies fixed source weights:
- Solana token names: 25%
- Solana NFT collections: 20%
- Solana domains: 15%
- Language.fi registry entries: 25%
- Gate.io token listings: 15%

Weighted Letter Usage formula:

```text
Weighted Letter Usage =
  (Solana Token Names × 0.25)
+ (Solana NFT Collections × 0.20)
+ (Solana Domains × 0.15)
+ (Language.fi Registry × 0.25)
+ (Gate.io Listings × 0.15)
```

### Oracle Update Cycle
Every few minutes the oracle:
1. Pulls latest available data from approved APIs/indexers.
2. Takes randomized samples from each source.
3. Normalizes names to uppercase.
4. Counts A-Z, 0-9, SPACE, and allowed symbols.
5. Compares current window to previous window.
6. Updates letter prices and usage stats.
7. Publishes oracle snapshot to the explorer.

### Settlement Proof Requirements
For real-money settlement, every oracle publication includes:
- Sample size
- Source URLs or source IDs
- Timestamp
- Normalization rules
- Duplicate removal rules
- Final count
- Previous count
- Change percentage
- Oracle signature

## Why It Matters

- **Novel Asset Class**: Letters as tradable assets with real usage data
- **Cross-Protocol Visibility**: Track letter usage across multiple blockchains
- **Derivatives Markets**: Weekly long/short positions on letter usage trends
- **Transparent Pricing**: Clear breakdown of how letter prices are calculated
- **Settlement Proofs**: On-chain verifiable outcomes for letter markets

## How It Makes Money

### Revenue Streams
1. **Trading Fees**: 0.25% fee on letter market transactions
2. **Position Fees**: 0.5% fee on weekly long/short letter positions
3. **Data API**: Subscription access to letter usage analytics ($49/mo)
4. **Enterprise Data**: Custom letter market reports for trading firms

### Conversion Strategy
- Free letter explorer view with live data
- Clear pricing on all markets
- One-click position taking
- Settlement proof transparency builds trust

## How It Works

### Main Explorer View
Each letter gets a card showing:
- Current Price (LGU)
- 24h Change
- Weekly Usage
- Rank
- Long/Short Interest
- Most Active Protocol
- Status

### Individual Letter Page
Full market page answering:
- How popular is this letter?
- Where is it being used?
- Is usage going up or down?
- What does it cost?
- Can users take a position?

### Protocol Breakdown
Usage by oracle source:
- Solana Token Names
- Solana NFT Collections
- Solana Domains
- Language.fi Registry Entries
- Gate.io Token Listings

### Weekly Letter Market
Derivatives-style long/short positions:
- Market: Long/Short [Letter] on [Protocol]
- Entry Snapshot: Usage count at position entry
- Settlement Rule: Wins if usage closes above/below last week
- Settlement: Sunday 23:59 UTC

### Sentence Staking
Stake whole sentences as character baskets:
- Sentence as letter index fund
- SPACE character as linguistic separator asset
- Stillness bonus: longer-held sentences earn higher multipliers
- Weekly performance based on character popularity
- Transfer penalties: moving resets stillness bonus
- Anti-spam rules: repetition penalties, diversity requirements
- Vaulted transfer option: preserve partial stillness on transfer

### Price Explanation Panel
Transparent pricing breakdown:
- Base Letter Price
- Protocol Usage Demand
- Gate.io Token Demand
- Registry Demand
- Hash Baseline Adjustment
- Popularity Tax
- Final Price

## How to Run It

### Prerequisites
```bash
# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys
```

### Local Development
```bash
# Start development server
npm run dev

# Access at http://localhost:3000
```

## How to Deploy It

### Quick Deploy (Vercel)
```bash
# Deploy to Vercel
vercel --prod
```

### Full Production Setup
1. Configure environment variables
2. Set up data sources (Gate.io API, blockchain RPCs)
3. Deploy to Vercel
4. Configure custom domain
5. Set up analytics

## Next Commercial Expansions

### Phase 1 (Immediate)
- Letter explorer with mock data
- Individual letter pages
- Price explanation panels
- Basic charts

### Phase 2 (1 month)
- Real data integration (Gate.io, blockchain RPCs)
- Weekly letter markets
- Settlement proofs
- Live price feeds

### Phase 3 (3 months)
- Real trading functionality
- Data API subscriptions
- Enterprise reports
- Mobile app
- Sentence staking with stillness mining

## Metrics We Track

- **Active Users**: Daily unique visitors
- **Letter Views**: Page views per letter
- **Position Volume**: Weekly long/short volume
- **Trading Volume**: Letter market transaction volume
- **Conversion Rate**: Explorer → Trader

## License

Proprietary - All rights reserved

## Contact

For partnership inquiries, contact: business@language.fi
