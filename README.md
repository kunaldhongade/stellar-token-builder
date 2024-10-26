# **Stellar Token Builder**

## **Overview**

LumiFi Token Builder is a smart contract project built using **Soroban SDK** on the Stellar blockchain. It enables users to create custom tokens, manage liquidity pools, and perform token swaps efficiently. This project offers a powerful toolset for decentralized finance (DeFi) applications and token-based ecosystems.

---

## 🎉 **Deployment Successful!**

🔗 [Contract on Stellar Expert](https://stellar.expert/explorer/testnet/contract/CBSZTRZYLMZI4PMU34MBO5KRCBQ3P4CSLIPV3QSHUITO7TTXFYOVK3QO)

✅ **Deployed Contract ID**: `CBSZTRZYLMZI4PMU34MBO5KRCBQ3P4CSLIPV3QSHUITO7TTXFYOVK3QO`

---

## **Features**

- **Token Creation:** Easily create custom tokens with specified names, symbols, and decimals.
- **Minting and Transfers:** Admins can mint tokens to users, and users can transfer tokens securely.
- **Liquidity Pools:** Add and withdraw liquidity in pools to facilitate decentralized trading.
- **Token Swaps:** Swap one token for another with minimal slippage, ensuring smooth transactions.
- **Secure Authorization:** Ensures that only authorized users can perform specific actions, like minting or transfers.

---

## **Contract Architecture**

1. **`Token` Contract:**
   - Handles token creation, minting, and transferring.
2. **`LiquidityPool` Contract:**
   - Manages liquidity addition and removal, enabling decentralized trading.
3. **`Swap` Contract:**
   - Allows users to swap one token for another securely.

---

## **How to Use**

### 1. **Setup Environment**

Make sure you have the following installed:

- **Rust**: [Install Rust](https://www.rust-lang.org/tools/install)
- **Soroban CLI**: [Install Soroban CLI](https://soroban.stellar.org/docs/getting-started/setup)

Clone the repository:

```bash
git clone https//www.github.com/kunaldhongade/stellar-token-builder
cd stellar-token-builder
```

---

### 2. **Build and Deploy Contracts**

Compile the smart contracts:

```bash
soroban contract build
```

Deploy the contracts using the Soroban CLI:

```bash
soroban contract deploy --wasm target/wasm32-unknown-unknown/release/lumifi_token_laucher.wasm
```

---

### 3. **Contract Functions**

#### **Token Contract**

- **Create Token**

  ```rust
  Token::create_token(env, admin_address, 18, "MyToken".into(), "MTK".into());
  ```

  - Creates a new token with specified name, symbol, and decimals.

- **Mint Tokens**

  ```rust
  Token::mint(env, user_address, 1000);
  ```

  - Mints `1000` tokens to the specified user.

- **Transfer Tokens**

  ```rust
  Token::transfer(env, from_address, to_address, 100);
  ```

  - Transfers `100` tokens from one user to another.

- **Check Balance**
  ```rust
  let balance = Token::balance(env, user_address);
  println!("User balance: {}", balance);
  ```
  - Retrieves the balance of a specific user.

#### **Liquidity Pool Contract**

- **Initialize Pool**

  ```rust
  LiquidityPool::initialize_liquidity(env, token_a_address, token_b_address);
  ```

  - Sets up a new liquidity pool for two tokens.

- **Deposit Liquidity**

  ```rust
  LiquidityPool::deposit(env, user_address, 500, 500);
  ```

  - Adds liquidity to the pool.

- **Withdraw Liquidity**
  ```rust
  let (amount_a, amount_b) = LiquidityPool::withdraw(env, user_address, 100);
  println!("Withdrawn: {} Token A, {} Token B", amount_a, amount_b);
  ```

#### **Swap Contract**

- **Perform Swap**
  ```rust
  Swap::swap(env, user_address, buy_token_address, sell_token_address, 100, 90);
  ```
  - Swaps `100` units of `sell_token` for `buy_token` with a minimum required `90`.

---

## **Example Workflow**

1. **Create a Token**: Use the `Token::create_token()` function to deploy a new token.
2. **Mint Tokens**: Mint tokens for yourself or users.
3. **Add Liquidity**: Add liquidity to a pool for decentralized trading.
4. **Swap Tokens**: Swap between tokens using the `Swap` contract.
5. **Withdraw Liquidity**: Withdraw liquidity from the pool when needed.

---

## **Error Handling**

- **Slippage Exceeded:** The buy amount is less than the minimum specified during the swap.
- **Insufficient Balance:** The user doesn't have enough tokens to complete a transaction.
- **Unauthorized Access:** The action requires admin authorization (e.g., minting tokens).

---

## **Security Considerations**

- **Authorization:** Uses Stellar’s native `require_auth()` to ensure only authorized users can perform sensitive operations.
- **Slippage Protection:** Prevents swaps that result in unfavorable rates for users.
- **Safe Storage:** Token balances are stored securely using the Soroban SDK's storage.

---

## **Contributing**

We welcome contributions to enhance the LumiFi Token Builder! Feel free to submit a pull request or open an issue.

---

## **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## **Acknowledgments**

Thanks to the Stellar Development Foundation for the amazing Soroban SDK, and the open-source community for their valuable contributions!
