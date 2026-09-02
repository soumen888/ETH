# Case Study: Multi-Hop Blockchain Forensic Source-of-Funds Analysis

> **Notice on Ongoing Research & Data Privacy:**
> Specific raw wallet addresses and transaction hashes have been intentionally redacted from this public case study due to active, ongoing investigation and privacy considerations. Only aggregated metrics, macro distributions, and sanitized graph topology are presented.

---

## Executive Summary

This case study demonstrates the methodology and findings of an automated, recursive **source-of-funds forensic investigation** conducted on a high-volume cryptocurrency destination cluster. 

The investigation examined **multiple inbound funding streams** totaling **33,000+ ETH** (historically transferred between Q4 2018 and Q4 2019). Through recursive transaction graph traversal (up to 16 hops) coupled with automated entity attribution intelligence, the origin of funds was unmasked from **0% direct identification to over 80% confirmed attribution**.

```text
========================================================================================
                      INVESTIGATION AT A GLANCE (PUBLIC OVERVIEW)
========================================================================================
• Target Destination        : 1 Primary Target Cluster (Sanitized)
• Inbound Funding Sources   : Multiple Unique Upstream Wallets
• Total Actual Capital      : 33,000+ ETH (Net Funds Investigated)
• Graph Flow Turnover       : 1,283,091 ETH (Cumulative Multi-Hop Transaction Volume)
• Direct Identification     : 0.0% of source wallets recognized at Hop 0
• Multi-Hop Attribution     : Over 80% of wallets | ~82% of volume (27,000+ ETH)
• Unattributed / Private    : ~20% of wallets | ~18% of volume ( 5,900+ ETH)
• Total Network Scope       : 1,804 Nodes | 2,227 Transaction Hops across 15 Depth Levels
========================================================================================
```

---

## 1. Capital Amount vs. Graph Flow Turnover (1.28M ETH Explained)

In multi-hop blockchain graph forensics, there is a fundamental difference between **Actual Capital Received** and **Cumulative Graph Flow Volume**:

```text
Actual Capital Investigated:  33,000+ ETH     ── Net funds arriving at the destination
Cumulative Graph Flow Volume: 1,283,091 ETH   ── Total turnover across all 2,227 graph edges
```

### Why does the Graph Flow exceed the Actual Inflow?
1. **Multi-Hop Edge Aggregation:** When a 100 ETH payment passes through 4 intermediary hops ($A \rightarrow B \rightarrow C \rightarrow D \rightarrow \text{Target}$), each hop edge records a 100 ETH transfer. The cumulative volume logged across the graph edges is $400\text{ ETH}$, even though the physical capital is only $100\text{ ETH}$.
2. **Exchange Omnibus Sweeps & Pool Liquidity:** When backtracking upstream into exchange hot wallets or mining pools, the algorithm captures large internal consolidation sweeps (some individual sweeps exceeded $100,000\text{ ETH}$ to $245,000\text{ ETH}$ within exchange treasury operations).
3. **Conclusion:** The actual money investigated is **33,000+ ETH**. The **1,283,091 ETH** figure represents the total transactional liquidity and movement examined across the entire upstream network.

---

## 2. High-Level Macro Category Breakdown

| Macro Category | Wallet Distribution | Net ETH Inflow | % of Total Capital | Primary Characteristics |
| :--- | :---: | :---: | :---: | :--- |
| **Tier-1 US Exchange (Coinbase)** | 51.55% | **21,000+ ETH** | **~63%** | Direct customer deposit accounts & omnibus sweeps |
| **Global Centralized Exchanges (CEX)** | 25.00% | **5,650+ ETH** | **~17%** | Binance, Kraken, OKX, Gemini, Bitfinex, Bittrex, etc. |
| **Unattributed / Private Addresses** | 19.96% | **5,900+ ETH** | **~18%** | Cold storage / virgin addresses with no prior on-chain history |
| **DeFi, Protocols & NFT** | 0.58% | **265+ ETH** | **< 1%** | Asset management protocols, decentralized liquidity, NFT mints |
| **Mining Pools & Validators** | 1.36% | **233+ ETH** | **< 1%** | Direct block reward distribution (Nanopool, Ethermine, Ethpool) |
| **Funds, Foundations & Identified Entities** | 1.55% | **268+ ETH** | **< 1%** | Institutional VCs, ecosystem foundation, known ecosystem figures |
| **Total** | **100.0%** | **33,000+ ETH** | **100.0%** | **Over 82% Attributed / ~18% Private** |

---

## 3. Discovered Entity Source Attribution

Below is the aggregated distribution of identified upstream entities (sanitized of specific private identifiers while preserving public institutional attribution):

| Rank | Identified Source Entity | Category / Type | Share of Capital | Avg Hop Depth |
| :---: | :--- | :--- | :---: | :---: |
| 1 | **Coinbase (Deposit Infrastructure)** | Tier-1 CEX | 62.76% (20,900+ ETH) | 1.09 |
| 2 | *Unattributed Private Cohort* | Private / Cold Wallets | 17.86% (5,900+ ETH) | 3.48 |
| 3 | **Binance** | Global CEX | 4.41% (1,470+ ETH) | 2.22 |
| 4 | **Kraken** | Tier-1 CEX | 1.74% (570+ ETH) | 2.43 |
| 5 | **OKX** | Global CEX | 1.40% (460+ ETH) | 2.25 |
| 6 | **Gemini** | Regulated US CEX | 1.17% (380+ ETH) | 2.14 |
| 7 | **Bilaxy** | Regional CEX | 1.12% (370+ ETH) | 3.00 |
| 8 | **Bitfinex** | Global CEX | 0.99% (320+ ETH) | 2.75 |
| 9 | **Bittrex** | Global CEX | 0.96% (320+ ETH) | 2.00 |
| 10 | **HTX (Huobi)** | Global CEX | 0.85% (280+ ETH) | 2.00 |
| 11 | **Upbit** | APAC CEX | 0.62% (200+ ETH) | 2.33 |
| 12 | **HitBTC** | Global CEX | 0.52% (170+ ETH) | 2.50 |
| 13 | **KuCoin** | Global CEX | 0.50% (160+ ETH) | 3.50 |
| 14 | **Bitkub** | APAC CEX | 0.49% (160+ ETH) | 5.00 |
| 15 | **Nanopool** | Mining Pool | 0.42% (140+ ETH) | 3.50 |
| 16 | **Crypto.com** | Global CEX | 0.42% (130+ ETH) | 2.00 |
| 17 | **Coinbase (Main Treasury)** | Tier-1 CEX | 0.40% (130+ ETH) | 1.00 |
| 18 | **Set Protocol** | DeFi Asset Management | 0.40% (130+ ETH) | 2.00 |
| 19 | **OpenSea Mint Contract** | NFT Smart Contract | 0.32% (100+ ETH) | 2.00 |
| 20 | **FBG Capital** | Crypto VC / Fund | 0.22% (70+ ETH) | 2.00 |
| 21 | **BitMart** | Global CEX | 0.18% (60+ ETH) | 2.00 |
| 22 | **CoinBene** | Regional CEX | 0.17% (55+ ETH) | 4.50 |
| 23 | **Bitso** | LATAM CEX | 0.16% (50+ ETH) | 2.00 |
| 24 | **Ethermine** | Mining Pool | 0.15% (50+ ETH) | 2.67 |
| 25 | **BW.com** | Global CEX | 0.15% (50+ ETH) | 2.00 |
| 26 | **bx.in.th** | CEX | 0.13% (40+ ETH) | 6.00 |
| 27 | **Ethpool** | Mining Pool | 0.12% (40+ ETH) | 3.00 |
| 28 | **Major Crypto Foundation Treasury** | Ecosystem Foundation | 0.12% (40+ ETH) | 2.00 |
| 29 | **Institutional VC Executive Wallet** | Identified Individual / Exec | 0.12% (40+ ETH) | 2.00 |
| 30 | **Public ENS Identity Group** | Web3 Identity / Domain | 0.12% (40+ ETH) | 2.00 |
| 31 | **Freewallet Service** | Hosted Wallet | 0.12% (40+ ETH) | 5.00 |
| 32 | **ShapeShift** | Instant DEX / Swap | 0.08% (25+ ETH) | 9.00 |
| 33 | **Alameda Research** | Quantitative Trading Firm | 0.07% (20+ ETH) | 2.00 |
| 34 | **Other Regional CEXs (15 Exchanges)** | Various CEX Providers | 0.72% (240+ ETH) | 2.00 – 6.00 |
| — | **Total Attributed + Unattributed** | — | **100.0% (33,000+ ETH)** | **—** |

---

## 4. Backtracking Depth & Path Dynamics

```text
Hops to Origin
Depth 1 (Direct CEX/Deposit) : [49.4% of Wallets] ══════════════════ [20,000+ ETH | ~60%]
Depth 2 (1 Intermediate Relay): [26.7% of Wallets] ═════════          [ 6,600+ ETH | ~20%]
Depth 3 (2 Intermediary Relays):[14.3% of Wallets] ═════              [ 3,700+ ETH | ~11%]
Depth 4 - 16 (Deep Layering) : [ 9.5% of Wallets] ═══                [ 2,900+ ETH |  ~9%]
```

### Forensic Routing Patterns Observed:
1. **Direct Deposit Infrastructure (49.4% of Wallets):** Funds sent directly from user deposit accounts managed by institutional custodians (average latency $< 24$ hours).
2. **Single-Hop Intermediary Transfer (26.7% of Wallets):** Standard user pattern: `Exchange Withdrawal -> Personal Cold/Hot Wallet -> Target Destination`.
3. **Multi-Hop Layered Routing (23.9% of Wallets):** Complex transaction layering through 2 to 15 intermediary nodes, including automated peel chains, multi-exchange bridging, and instant swap protocols (e.g., ShapeShift at 9 hops; Bitkub at 5 hops).

---

## 5. Network Graph & Cluster Characteristics

* **Graph Breadth:** The total reverse trace graph spans **1,804 unique wallet nodes** interconnected via **2,227 transaction edges**.
* **Intermediary Relay Hubs:** **374 nodes** functioned as multi-path relays (receiving funds from upstream exchange hot wallets and distributing them across multiple secondary wallets).
* **Super-Cluster Analysis:** A single interconnected network component linked a large portion of the feeder wallets together through common upstream exchange consolidation infrastructure, demonstrating high operational coordination across depositors.
* **Cold Storage Inflow:** The unattributed wallets stopped at addresses that had never received an incoming transaction prior to funding the target (representing virgin addresses, pre-sale allocations, or private offline generation).

---

## 6. Summary of Key Findings

* **Overwhelming Institutional / CEX Predominance:** **~80% of all capital** originated from centralized exchanges (led by Coinbase at ~63% and Binance/Kraken/Gemini at ~17%).
* **Effective Multi-Hop Resolution:** While 0% of wallets were directly identifiable at the destination layer, recursive tracing successfully solved the source-of-funds for **over 82% of the overall volume**.
* **Clean Trace Boundaries:** Only 1 circular loop and 1 depth limit were encountered across the entire multi-wallet graph, proving high tree-search convergence.
* **Residual Investigation Focus:** The remaining **~18% (5,900+ ETH)** represents isolated, non-exchange private reserves suitable for specialized off-chain / pre-sale cross-referencing.
