# Deployment Parameters

This page describes the concrete configuration parameters of the mainnet deployment of the Forex AMM.

### Back stop pool

The Backstop Pool token is USDC. The maximum amount of pool tokens is 30,000 USDC.

### Swap pools

The Forex AMM comprises the following four Swap Pools.

| Swap Pool | Asset    | Max Limit (\~$15k) |
| --------- | -------- | ------------------ |
| 1         | USDC     | 15000              |
| 2         | DOT      | 3500               |
| 3         | EURC.s   | 13500              |
| 4         | USDC.axl | 15000              |

### Protocol Treasury

The protocol treasury has the address `6bBWiUZpDKcecCbP3kjfYTRNToj8zHKugFxNs6yAP4j1u2ib`

### Insurance fees

The insurance fee is the fee used for [Backstop Redeems](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/lp-user-guide/cross-interaction).

| Asset    | Fee  |
| -------- | ---- |
| USDC.axl | 0.5% |
| USDC     | 0.5% |
| DOT      | 2%   |
| EUR.s    | 0.5% |

### Swap fees

The following table lists the total fees used for swaps.

| Asset    | Fee   |
| -------- | ----- |
| USDC.axl | 0.15% |
| USDC     | 0.15% |
| DOT      | 0.25% |
| EUR.s    | 0.15% |

### Timelock

A Backstop Redeem for a Swap Pool is only possible 14 days after your last deposit into the Swap Pool.

### Maximum coverage ratio

Swap Pools deposits cannot raise their coverage ratio above 200%.

### Slippage curve

All details about the used slippage curves can be found on the page about [Coverage Ratio and Slippage](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/coverage-ratio-and-slippage).&#x20;

## Future Roadmap

* Increasing pool caps
* Adding support for more swap pool tokens
* Backstop pool supporting more tokens
* Integrating Forex AMM into Vortex for quotes&#x20;

