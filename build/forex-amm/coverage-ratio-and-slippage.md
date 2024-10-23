# Coverage Ratio and Slippage

### Coverage Ratio

Each Swap Pool has two key parameters that evolve over time:

* **Reserves**: The amount of tokens available in the pool for swaps.
* **Liabilities**: The amount of tokens the Swap Pool owes to liquidity providers (LPs). If all LPs return their LP tokens to withdraw liquidity, they are entitled to receive this total amount.

The reserves fluctuate due to swap activities, while liabilities change as LPs deposit or withdraw liquidity.

If reserves fall below liabilities, the Swap Pool cannot immediately fulfill the full amount owed to LPs. To prevent this, the Forex AMM is designed to keep reserves aligned with liabilities as closely as possible.

This alignment is expressed through the _Coverage Ratio_ (CR), defined as: CR = Reserves / Liabilities

* A CR below 100% indicates insufficient coverage of liabilities.
* A CR above 100% indicates an excess concentration of liquidity in the Swap Pool.

The ideal CR is 100%, representing a balanced state where reserves perfectly match liabilities.

### Slippage Curve

To maintain balance in the Swap Pools (i.e., a CR of 100%), the Forex AMM incentivizes users to make swaps that move the CR closer to this target. The exchange rate is adjusted accordingly—becoming more favorable when the CR approaches 100% and less favorable when the CR deviates further from 100%.

Each swap involves two Swap Pools: the input Swap Pool and the output Swap Pool. The change in the CR of each pool influences the exchange rate. Consider the following example:

* The CR of the input Swap Pool changes from 50% to 75%.
* The CR of the output Swap Pool changes from 100% to 75%.

In this case:

* The input Swap Pool’s CR moves closer to 100%, positively impacting the exchange rate and increasing the output amount by, say, 0.45%.
* The output Swap Pool’s CR moves away from 100%, negatively impacting the exchange rate and decreasing the output amount by, say, 0.14%.

As a result, the overall effect is that the output amount is 0.31% above the market rate.

The relationship between CR changes and the effective exchange rate is mathematically expressed through a _slippage curve_. Each Swap Pool has its own slippage curve, which determines how it responds to changes in its CR. The Forex AMM utilizes different slippage curves for stablecoin Swap Pools and non-stablecoin Swap Pools to account for their respective volatility risks.

### Example Slippage Curves

The slippage curve of a Swap Pool describes its influence on the exchange rate based on the CR before and after a swap, making it a function of two parameters. Below, we illustrate the slippage curve used by the Forex AMM for stablecoin Swap Pools, showing its values for various combinations of initial and final CRs.

The first table shows the slippage curve that the Forex AMM uses for stable coin Swap Pools.

<table><thead><tr><th width="153"></th><th width="116">End CR 0</th><th width="123">End CR 0.2</th><th width="124">End CR 0.5</th><th width="127">End CR 0.75</th><th width="102">End CR 1</th><th width="118">End CR 1.5</th><th>End CR 2</th></tr></thead><tbody><tr><td>Start CR 0</td><td><strong>0%</strong></td><td><strong>1.2%</strong></td><td><strong>0.98%</strong></td><td><strong>0.8%</strong></td><td><strong>0.64%</strong></td><td><strong>0.34%</strong></td><td><strong>0.07%</strong></td></tr><tr><td>Start CR 0.2</td><td>-<strong>1.22%</strong></td><td><strong>0%</strong></td><td><strong>0.83%</strong></td><td><strong>0.66%</strong></td><td><strong>0.5%</strong></td><td><strong>0.2%</strong></td><td>-<strong>0.06%</strong></td></tr><tr><td>Start CR 0.5</td><td>-<strong>0.99%</strong></td><td>-<strong>0.84%</strong></td><td><strong>0%</strong></td><td><strong>0.45%</strong></td><td><strong>0.3%</strong></td><td><strong>0.02%</strong></td><td>-<strong>0.23%</strong></td></tr><tr><td>Start CR 0.75</td><td>-<strong>0.81%</strong></td><td>-<strong>0.66%</strong></td><td>-<strong>0.45%</strong></td><td><strong>0%</strong></td><td><strong>0.14%</strong></td><td>-<strong>0.13%</strong></td><td>-<strong>0.37%</strong></td></tr><tr><td>Start CR 1</td><td>-<strong>0.64%</strong></td><td>-<strong>0.5%</strong></td><td>-<strong>0.3%</strong></td><td>-<strong>0.14%</strong></td><td><strong>0%</strong></td><td>-<strong>0.26%</strong></td><td>-<strong>0.5%</strong></td></tr><tr><td>Start CR 1.5</td><td>-<strong>0.34%</strong></td><td>-<strong>0.2%</strong></td><td>-<strong>0.02%</strong></td><td><strong>0.13%</strong></td><td><strong>0.26%</strong></td><td><strong>0%</strong></td><td>-<strong>0.74%</strong></td></tr><tr><td>Start CR 2</td><td>-<strong>0.07%</strong></td><td><strong>0.06%</strong></td><td><strong>0.23%</strong></td><td><strong>0.37%</strong></td><td><strong>0.5%</strong></td><td><strong>0.73%</strong></td><td><strong>0%</strong></td></tr></tbody></table>

The second table shows the slippage curve that the Forex AMM employs for non-stable coin Swap Pools.

<table><thead><tr><th width="163"></th><th width="111">End CR 0</th><th width="117">End CR 0.2</th><th width="117">End CR 0.5</th><th width="125">End CR 0.75</th><th>End CR 1</th><th width="113">End CR 1.5</th><th>End CR 2</th></tr></thead><tbody><tr><td>Start CR 0</td><td><strong>0%</strong></td><td><strong>4.92%</strong></td><td><strong>3.95%</strong></td><td><strong>3.22%</strong></td><td><strong>2.55%</strong></td><td><strong>1.38%</strong></td><td><strong>0.38%</strong></td></tr><tr><td>Start CR 0.2</td><td>-<strong>5.18%</strong></td><td><strong>0%</strong></td><td><strong>3.3%</strong></td><td><strong>2.6%</strong></td><td><strong>1.96%</strong></td><td><strong>0.83%</strong></td><td>-<strong>0.13%</strong></td></tr><tr><td>Start CR 0.5</td><td>-<strong>4.11%</strong></td><td>-<strong>3.42%</strong></td><td><strong>0%</strong></td><td><strong>1.76%</strong></td><td><strong>1.16%</strong></td><td><strong>0.09%</strong></td><td>-<strong>0.81%</strong></td></tr><tr><td>Start CR 0.75</td><td>-<strong>3.33%</strong></td><td>-<strong>2.67%</strong></td><td>-<strong>1.79%</strong></td><td><strong>0%</strong></td><td><strong>0.55%</strong></td><td>-<strong>0.46%</strong></td><td>-<strong>1.33%</strong></td></tr><tr><td>Start CR 1</td><td>-<strong>2.62%</strong></td><td>-<strong>2%</strong></td><td>-<strong>1.17%</strong></td><td>-<strong>0.55%</strong></td><td><strong>0%</strong></td><td>-<strong>0.97%</strong></td><td>-<strong>1.8%</strong></td></tr><tr><td>Start CR 1.5</td><td>-<strong>1.4%</strong></td><td>-<strong>0.84%</strong></td><td>-<strong>0.09%</strong></td><td><strong>0.46%</strong></td><td><strong>0.96%</strong></td><td><strong>0%</strong></td><td>-<strong>2.63%</strong></td></tr><tr><td>Start CR 2</td><td>-<strong>0.38%</strong></td><td><strong>0.13%</strong></td><td><strong>0.81%</strong></td><td><strong>1.31%</strong></td><td><strong>1.77%</strong></td><td><strong>2.56%</strong></td><td><strong>0%</strong></td></tr></tbody></table>
