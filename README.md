Wallet Score Project
Overview
This project analyzes 103 wallet addresses and assigns each a credit score (0–1000) based on their Ethereum mainnet activity.
The scoring is based on their transaction volume, activity frequency, and contract interactions.

What This Project Does
Reads a list of 103 wallet addresses from Wallet_id.csv.

Checks if these wallets have any activity:

First, it checks Polygon network (via free APIs) → No transactions found.

Then, it checks Ethereum mainnet, where activity is found.

Fetches all transactions for each wallet using the Etherscan API:

ETH or token transfers.

Contract calls (DeFi or smart contract interactions).

Processes and cleans the data:

Counts the number of transfers.

Counts the number of contract calls.

Calculates total transaction volume (ETH).

Computes transaction count and active days (days the wallet was used).

Groups wallets into 4 clusters using K-Means clustering.

Assigns each wallet a credit score (0–1000) based on cluster behavior.

Why Ethereum Network?
The wallets were first checked on Polygon network.

Since no activity was detected, the analysis was done on the Ethereum mainnet, where these wallets had actual transactions.

