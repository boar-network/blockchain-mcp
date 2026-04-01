# Prompt Cookbook

Copy-paste these prompts into your AI agent to test Boar MCP tools. Each workflow shows the prompt, which tools the agent will call, and what to expect.

---

## 1. Debug a Failed Transaction

**Endpoint needed:** `/basic` + `/advanced`

**Prompt:**
> Transaction 0x596030fc0f8e2ccf193ce5f2b661446d48645da5621d02938621e2c1b6b93e2a failed on Ethereum. Why did it revert?

**What the agent does:**
1. Calls `eth_get_transaction_receipt` to confirm the transaction failed (status `0x0`) and extract revert data
2. Calls `eth_get_transaction` to inspect the input data (this is a Uniswap V3 Router `multicall`)
3. Calls `eth_decode_revert` with the revert data to get a human-readable error message
4. If the error selector is unknown, calls `eth_lookup_selector` to identify the custom error signature

**Expected output:** The agent will explain that this Uniswap V3 swap failed because the transaction deadline had passed ("Transaction too old"). It will show the failed status, gas consumed, and the decoded revert reason.

---

## 2. Inspect an Unknown Contract

**Endpoint needed:** `/basic` + `/advanced`

**Prompt:**
> What does the contract at 0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48 do? Show me its interface.

**What the agent does:**
1. Calls `eth_get_code` to confirm the address is a contract (not an EOA)
2. Calls `eth_get_abi` to fetch the verified ABI from Sourcify
3. Analyzes the ABI to describe the contract's functions and events
4. Optionally calls `eth_decode_calldata` to decode specific transaction inputs

**Expected output:** A description of the contract's interface (this is USDC), including its main functions like `transfer`, `approve`, `balanceOf`, and key events like `Transfer` and `Approval`.

---

## 3. Check a Wallet's Token Position

**Endpoint needed:** `/basic`

**Prompt:**
> How much USDC does 0x28C6c06298d514Db089934071355E5743bf21d60 hold?

**What the agent does:**
1. Calls `eth_get_token_balance` with the USDC contract (`0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48`) and the wallet address
2. Returns the formatted balance with symbol and decimals
3. Optionally calls `eth_get_token_info` for full token metadata (name, total supply)

**Expected output:** The agent will show this Binance hot wallet's USDC balance formatted with 6 decimals, along with the token symbol.

---

## 4. Trace a Bitcoin Address

**Endpoint needed:** `/basic`

**Prompt:**
> Show me the balance and recent activity for 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa

**What the agent does:**
1. Calls `btc_get_balance` for confirmed and unconfirmed balance in satoshis
2. Calls `btc_get_utxos` to list unspent outputs
3. Calls `btc_get_history` to show recent transaction activity with heights and tx hashes

**Expected output:** This is Satoshi Nakamoto's genesis address. The agent will show the balance (many small donations over the years), UTXOs, and transaction history.

---

## 5. Decode On-Chain Events

**Endpoint needed:** `/basic` + `/advanced`

**Prompt:**
> What events did the USDC contract (0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48) emit in the latest block on Ethereum?

**What the agent does:**
1. Calls `eth_get_block` with `"latest"` to get the current block number
2. Calls `eth_get_logs` with the USDC contract address and the block range
3. Calls `eth_get_abi` to fetch the USDC ABI from Sourcify
4. For each raw log, calls `eth_decode_log` with the ABI to produce named event fields (e.g., Transfer: from, to, value)

**Expected output:** A list of decoded events — mostly `Transfer` events showing sender, recipient, and USDC amounts.

---

## 6. Resolve an ENS Identity

**Endpoint needed:** `/basic`

**Prompt:**
> Who is vitalik.eth? Show me their ETH balance and any tokens.

**What the agent does:**
1. Calls `eth_resolve_ens` with `"vitalik.eth"` to get the address (`0xd8dA6BF26964aF9D68eC99A6d99030B4ec93B700`)
2. Calls `eth_get_balance` with the resolved address to get ETH balance
3. Optionally calls `eth_get_token_balance` for specific tokens
4. The reverse also works: given an address, `eth_lookup_address` returns the primary ENS name

**Expected output:** Vitalik's Ethereum address, ETH balance, and any requested token balances — all resolved from the human-readable ENS name.
