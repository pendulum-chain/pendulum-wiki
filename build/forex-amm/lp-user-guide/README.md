---
description: User guide for liquidity providers
---

# LP User Guide

Liquidity Providers (LPs) can provide liquidity to all Swap Pools and the Backstop Pool within the Forex AMM. Each Swap Pool accepts liquidity for a specific token, referred to as the _pool token_ for that Swap Pool. The Backstop Pool, however, only accepts USDC.

When LPs deposit liquidity into any of these pools, they receive LP tokens for the respective pool. These LP tokens can later be redeemed to withdraw the liquidity they initially provided.

LPs can interact with the Forex AMM pools in six different ways:

* [**Swap Pools**](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/lp-user-guide/swap-pools):
  * **Deposit Liquidity**: Deposit pool tokens and receive LP tokens in return.
  * **Withdraw Liquidity**: Redeem LP tokens to withdraw pool tokens.
* [**Backstop Pool**](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/lp-user-guide/backstop-pool):
  * **Deposit Liquidity**: Deposit USDC (Backstop Pool tokens) and receive LP tokens in return.
  * **Withdraw Liquidity**: Redeem LP tokens to withdraw USDC from the Backstop Pool.
* [**Cross Interaction**](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/lp-user-guide/cross-interaction):
  * **Backstop Redeem**: redeem Swap Pool LP tokens and withdraw Backstop Pool tokens
  * **Backstop Drain**: redeem Backstop Pool LP token and withdraw Swap Pool tokens

