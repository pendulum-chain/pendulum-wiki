# Architecture

The Forex AMM distinguishes itself from conventional AMMs by using single-sided liquidity pools, known as Swap Pools. These pools are complemented by a Backstop Pool, which mitigates most of the economic risks associated with liquidity provision in the system.

Swaps occur directly between the Swap Pools, allowing exchanges between any pair of these pools. Since liquidity is supplied on a single-sided basis per Swap Pool instead of per asset pair, it avoids fragmentation and maximizes the availability of liquidity across various assets.

The Backstop Pool does not participate in swaps; its primary function is to provide coverage for Swap Pool LPs. If a Swap Pool lacks sufficient coverage, LPs can withdraw assets from the Backstop Pool to ensure their claims are fulfilled.

### Swap pools

Each tradeable asset has its own Swap Pool. Liquidity providers can deposit liquidity separately into each Swap Pool and receive LP tokens in return, which they can later redeem to withdraw their liquidity.

To swap assets, users select a pair of Swap Pools, deposit a specific amount of tokens into the first pool, and receive an equivalent amount of tokens from the second Swap Pool. The effective exchange rate will closely align with the market rate of off-chain markets provided by real-time price feed oracles.&#x20;

### Swap algorithm

The effective exchange rate may slightly differ from the market rate due to:

* Fees distributed among Swap Pool LPs, the Backstop Pool LPs, and the protocol treasury.
* A slippage mechanism that incentivizes balance within Swap Pools.

The slippage mechanism operates as follows: each Swap Pool tracks two key amounts—the _liability_ (the total volume of liquidity provided by LPs) and the _reserve_ (the current amount of liquidity available in the pool). This is a simplified definition. Initially, both values are equal, but the reserve fluctuates as swaps occur.

The ratio of reserve to liability is known as the _Coverage Ratio_ (CR). A CR of 100% indicates that the Swap Pool is balanced. If the CR is below 100%, the pool has less liquidity than what LPs have provided. Conversely, a CR above 100% suggests an excess concentration of liquidity in that Swap Pool.

The Forex AMM incentivizes users to perform swaps that restore balance in the Swap Pools. Swaps that bring CRs closer to 100% reward users with a more favorable effective exchange rate, while swaps that move CRs further from 100% are penalized with a less favorable rate.

Mathematically, this incentive is governed by a _slippage curve_, which defines how changes in the CR affect the exchange rate.

### Backstop pool&#x20;

The Forex AMM features a single Backstop Pool. Similar to Swap Pools, LPs can contribute liquidity to the Backstop Pool in the form of a USD stablecoin and receive Backstop Pool LP tokens in return.

The Backstop Pool covers the residual economic risk of the Swap Pools through two mechanisms that connect Swap Pools with the Backstop Pool:

* **Backstop Pool Redeem**: This mechanism can be used when a Swap Pool’s CR falls below 100%. The Swap Pool LP returns LP tokens to the Swap Pool but, instead of receiving liquidity from the Swap Pool itself, they receive tokens from the Backstop Pool. This restores the CR to 100% by reducing the Swap Pool’s liability without affecting its reserve.
* **Backstop Drain**: This mechanism is possible when a Swap Pool’s CR exceeds 100%. The Backstop Pool LP returns LP tokens to the Backstop Pool but, instead of receiving liquidity from the Backstop Pool, they receive tokens from the Swap Pool. This action restores the CR to 100% by decreasing the reserve of the Swap Pool without changing its liability.
