# AAA25test Smart Contract

## Overview
`AAA25test` is an ERC-20 token designed with additional features to enhance transaction management, tokenomics, fees, rewards, and liquidity management. This document provides a comprehensive breakdown of its functions and features in simple terms.

## Key Components and Functions

### Token Information
- **`name()`**: Returns "AAA25", the name of the token.
- **`symbol()`**: Provides "AAA25", the trading symbol of the token.
- **`decimals()`**: Specifies the token's divisibility, set to 9 decimal places.

### Supply Management
- **`totalSupply()`**: Displays the total supply of tokens in existence.
- **`balanceOf(account)`**: Shows the number of tokens a specific account holds.

### Trading and Transfers
- **`transfer(sender, recipient, amount)`**: Allows a user to send a specified amount of tokens to another user.
- **`transferFrom(sender, recipient, amount)`**: Facilitates a transaction initiated by a third party, given they have the necessary permissions.
- **`approve(spender, amount)`**
- **`increaseAllowance(spender, addedValue)`**
- **`decreaseAllowance(spender, subtractedValue)`**: These functions manage how one account can spend tokens on behalf of another through allowances.

### Fees and Rewards
- Implements a system for collecting various types of fees (liquidity, NFT rewards, operational, and development fees) during transactions, which differ between buys and sells (`taxes` and `sellTaxes`).
- **`launchtax`**: Applies special taxes at the start of trading to stabilize initial market activity.

### Liquidity and Swapping
- **`swapAndLiquify()`**: This function is triggered automatically under certain conditions to exchange tokens for another blockchain currency (like Ethereum or BNB) and add them to a liquidity pool, essential for maintaining "cash flow" on exchanges.

### Special Wallets
- Designated wallets such as `nftRewardWallet`, `opsWallet`, and `devWallet` collect specific transaction fees. These addresses can be changed as needed.

### Access Controls
- **`onlyOwner`**: Restricts access to most critical functions to the contract's owner.
- **`EnableTrading()`**: Trading is initially disabled and can be enabled by the owner, which also activates swap functionalities.

### Additional Features
- **`burn(value)`**: Enables the owner to permanently reduce the supply, potentially increasing the token's value.
- **`rescuePLS(weiAmount)`**: Allows the owner to withdraw any Ethereum accidentally sent to the contract.
- **`rescueERC20Tokens(tokenAddr, to, amount)`**: Permits the recovery of any ERC-20 tokens sent to the contract in error.

## Event Handling
- Events such as `Transfer`, `Approval`, `FeesChanged`, and `Burn` are emitted to log activities on the blockchain, ensuring transparency and aiding in tracking changes within the contract.

## Detailed Functionality

### Core ERC-20 Functions
- **`transfer(recipient, amount)`**
- **`approve(spender, amount)`**
- **`transferFrom(sender, recipient, amount)`**
- **`allowance(owner, spender)`**
- **`increaseAllowance(spender, addedValue)`**
- **`decreaseAllowance(spender, subtractedValue)`**

### Tokenomics and Fee Management
- **`setMaxTxAmount(_maxTxAmount)`**: Limits the maximum transaction amount.
- **`setBuyTaxes(...)`** and **`setSellTaxes(...)`**: Adjust fees for buying and selling transactions.
- **`includeInFee(address)`** and **`excludeFromFee(address)`**: Manage fee exemptions.
- **`excludeFromReward(address)`** and **`includeInReward(address)`**: Manage reward exemptions.

### Liquidity Management
- **`swapAndLiquify(contractBalance, temp)`**
- **`addLiquidity(tokenAmount, plsAmount)`**
- **`swapTokensForPLS(tokenAmount)`**

### Trading Control
- **`EnableTrading()`**
- **`updateSwapTokensAtAmount(amount)`**
- **`updatedeadline(_deadline)`**
- **`burn(_value)`**

### Wallet Management
- **`updateNftRewardWallet(newWallet)`**, **`updateDevWallet(newWallet)`**, **`updateOpsWallet(newWallet)`**

### Rescue Operations
- **`rescuePLS(weiAmount)`**
- **`rescueERC20Tokens(tokenAddr, to, amount)`**

## Event Emitters
- **`Transfer(from, to, value)`**
- **`Approval(owner, spender, value)`**
- **`Burn(burner, value)`**
- **`FeesChanged()`**
- **`UpdatedRouter(oldRouter, newRouter)`**

This contract provides the necessary tools for managing the AAA25 token's economy, ensuring liquidity, enabling trading, adjusting economic parameters, and maintaining governance structure compliance as specified by the contract's owner.
