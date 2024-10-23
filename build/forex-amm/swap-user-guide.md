# Swap User Guide

### Understanding Swap Pools

Each swap involves a pair of assets, each managed by a separate Swap Pool. The Pendulum Portal provides an [overview of all available Swap Pools](https://portal.pendulumchain.org/pendulum/nabla/swap-pools), showing the following details for each:

* **Name**: The name of the token managed by this Swap Pool.
* **Pool Liabilities**: The total liquidity provided for this pool (this is a simplified definition).
* **Reserves**: The amount of tokens currently available in the pool for swaps.
* **APR**: The estimated annual percentage rate for liquidity providers.
* **My Pool Amount**: The number of LP tokens you own for that Swap Pool.

For users who want to execute a swap, the most important information is the liabilities and reserves of the pools. The ratio of reserves to liabilities is called the _Coverage Ratio_ (CR) of the respective Swap Pool. Each swap impacts the CR of the two Swap Pools involved: if you trade token A for token B, the CR of token A’s Swap Pool will increase (as its reserves increase), while the CR of token B’s Swap Pool will decrease (as its reserves decrease).

The effective exchange rate of a swap is influenced by the changes in the CRs of the involved Swap Pools. If either CR deviates further from 100%, the exchange rate becomes less favorable; if either CR moves closer to 100%, it becomes more favorable. The overall effect on the exchange rate is determined by the combined impact of both Swap Pools.&#x20;

For more information on these effects, refer to the explanation of [coverage ratios and slippage](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/coverage-ratio-and-slippage).

### How to Execute a Swap

To execute a swap, navigate to [the Forex AMM area of the Pendulum Portal](https://portal.pendulumchain.org/pendulum/nabla/swap). The swap interface works as follows:

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-18 at 09.35.53.png" alt=""><figcaption><p>Screenshot of the swap UI</p></figcaption></figure>

1. **Select the input token** using the drop-down menu in the top-right corner.
2. **Enter the input amount**. The value of this amount, expressed in USD, is displayed below the input field.
3. **View your current balance** of the input token and the maximum amount you can use. You can click the "50%" or "MAX" button to select 50% or 100% of your available balance as the input amount.
4. **Select the output token** using the drop-down menu. Your current balance of this token is shown below the drop-down.
5. **Review the estimated output amount** and its value in USD.
6. **Check the estimated exchange rate**.
7. For more details about the swap, click on the rounded arrow icon:
   * The expected output amount
   * The minimum output amount you will receive based on the current slippage tolerance. If the output amount falls below this minimum, the swap will not proceed. You can set the slippage tolerance by clicking the settings icon (see point 8).
   * The swap fee: this is the fee distributed to liquidity providers and the protocol treasury. This fee is already factored into the expected output amount.
8. **Adjust the slippage tolerance and transaction deadline** by clicking the settings (cogwheel) icon. The slippage tolerance sets the minimum output amount; the swap will be canceled if the output falls below this threshold. Additionally, the swap will not be executed if it isn’t confirmed on-chain within the specified transaction deadline.
9. **Execute the swap** by clicking the button. In most cases, you will need to approve the input amount first (the button will read "Approve"). After approval, click the button again to submit the swap transaction (the button will then read "Swap").

If the transaction is successful, a "Transaction successful" message will appear, confirming that your tokens have been swapped.

