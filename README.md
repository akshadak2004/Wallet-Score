# Wallet-Score
What this project does
Reads a list of 103 wallet addresses from a CSV file.

Checks if these wallets have any activity:

First, it tried Polygon network (via APIs) → No transactions found.

Then, it checked Ethereum mainnet, where most transactions were found.

Fetches all transactions (ETH transfers + contract interactions) for each wallet using the Etherscan API.

Processes and cleans the data:

Counts the number of token transfers.

Counts the number of contract calls (smart contract interactions).

Calculates total transaction volume (in ETH).

Calculates transaction count and active days (number of days a wallet was used).

Clusters the wallets into 4 groups based on their behavior using K-Means clustering.

Assigns a score (0–1000) to each wallet based on which cluster it belongs to.

Why Ethereum network, not Polygon?
The wallet list was checked on Polygon first, but no transaction history was found.

Therefore, all scoring is based on Ethereum mainnet transactions, where activity exists.

What transactions were considered?
We considered two types of activity:

Transfers → Normal ETH/token movements (num_transfers).

Contract Calls → Interactions with DeFi or other smart contracts (num_contract_calls).

The action is marked as:
action = "transfer" if int(tx["value"]) > 0 else "contract_call"
If the transaction involves moving tokens (value > 0), it’s a transfer.

If no token transfer but a contract is called, it’s a contract interaction.

Columns we used
For each wallet, we kept:

'_id', 'userWallet', 'network', 'protocol', 'txHash', 'logId',
'timestamp', 'blockNumber', 'action', 'actionData', '__v',
'createdAt', 'updatedAt'

Then we aggregated features:

'userWallet', 'num_transfers', 'num_contract_calls',
'total_volume_eth', 'tx_count', 'active_days', 'cluster',
'credit_score', 'pca1', 'pca2'
How the credit score is given
The wallets were divided into 4 clusters (0–3) based on:

How many transfers they did.

How many contract calls they made.

Total volume in ETH.

Number of active days.

Total transactions.

Each cluster represents a behavior type:

Cluster 1 (Score 1000) → Most Active User.

Cluster 2 (Score 800) → Active and high-volume users.

Cluster 0 (Score 650) → Low or casual activity.

Cluster 3 (Score 400) → Riskier or mixed-behavior wallets (possibly abnormal).

Outputs
wallet_scores.csv → Wallet address, cluster, and credit score.

Cluster summaries (average activity metrics per cluster).

Visualizations (optional) like heatmaps and PCA scatter plots for analysis.

How to run
Put your wallet list in Wallet_id.csv (with a wallet_id column).
Run the script:
python fetch_and_score_wallets.py
Results will be saved in:
all_wallet_transactions.json (raw data).
wallet_scores.csv (final scores).
