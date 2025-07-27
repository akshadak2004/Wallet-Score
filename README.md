##Overview
This project analyzes 103 wallet addresses and assigns each a credit score (0–1000) based on their Ethereum mainnet activity.
The scoring is based on their transaction volume, activity frequency, and contract interactions.

##What This Project Does
1.Reads a list of 103 wallet addresses from Wallet_id.csv.
2.Checks if these wallets have any activity:
First, it checks Polygon network (via free APIs) → No transactions found.
Then, it checks Ethereum mainnet, where activity is found.
3.Fetches all transactions for each wallet using the Etherscan API:
ETH or token transfers.
Contract calls (DeFi or smart contract interactions).
4.Processes and cleans the data:
Counts the number of transfers.
Counts the number of contract calls.
Calculates total transaction volume (ETH).
Computes transaction count and active days (days the wallet was used).
5.Groups wallets into 4 clusters using K-Means clustering.
6.Assigns each wallet a credit score (0–1000) based on cluster behavior.

