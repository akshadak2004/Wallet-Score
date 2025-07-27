# Wallet-Score

## Overview
This project checks 103 wallet addresses for activity on **Ethereum** networks, fetches their transactions, and assigns a **credit score (0–1000)** based on behavior.

## What It Does
- Fetches **ETH/token transfers** and **smart contract interactions**.
- Calculates:
  - Transfers count (`num_transfers`)
  - Contract call count (`num_contract_calls`)
  - Total ETH volume
  - Transaction count
  - Active days
- Groups wallets into **4 clusters** using K-Means.
- Assigns a **credit score** based on activity.

## Why Ethereum?
Polygon was checked first (no transactions found).  
All scores are based on **Ethereum mainnet transactions**, where wallets are active.

## How Scores Are Assigned
Wallets are clustered by behavior:
- **Cluster 1 → 1000 (Most Active)**  
- **Cluster 2 → 800 (Active, High Volume)**  
- **Cluster 0 → 650 (Low/Casual)**  
- **Cluster 3 → 400 (Risky or Irregular)**  

Scores are stored in `wallet_scores.csv`.

## Types of Transactions Considered

Two main categories were analyzed:

- **Transfers** – Standard ETH/token transfers.
- **Contract Calls** – Smart contract interactions (e.g., DeFi lending/borrowing, swaps).

## Files Produced
- `all_wallet_transactions.json` → Raw transaction data.  
- `wallet_scores.csv` → Final wallet scores and clusters.

## How to Run
1. Add your wallet list to `Wallet_id.csv`:
2. run wallet.py
3. wallet_scores.csv – Final scores and cluster assignments for each wallet.
4. all_wallet_transactions.json – Full transaction history.
