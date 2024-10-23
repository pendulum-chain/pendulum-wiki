# Cross Interaction

### Backstop Redeem

A Backstop Redeem from a Swap Pool is only possible if the [CR (coverage ratio) of the Swap Pool ](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/coverage-ratio-and-slippage)is below 100% and your last deposit into the Swap Pool was more than 14 days ago.

To redeem from the Backstop Pool, navigate to [the Swap Pool overview](https://portal.pendulumchain.org/pendulum/nabla/swap-pools), select the Swap Pool, and click the "Withdraw" button. **This will open a popup. If a backstop redeem is available for this Swap Pool, a link labeled "Redeem from Backstop Pool"** will appear at the bottom of the popup.

The user interface for Backstop Redeems includes the following information:

<figure><img src="../../../.gitbook/assets/Screenshot 2024-10-21 at 04.49.04.png" alt=""><figcaption><p>Backstop Redeem UI</p></figcaption></figure>

1. The number of Swap Pool LP tokens you own, representing the maximum amount you can redeem.
2. Your current balance of Backstop Pool tokens.
3. **Enter the amount** of Swap Pool LP tokens you wish to redeem.
4. The number of Backstop Pool tokens you will receive based on the amount you redeem.
5. The fee associated with the backstop redeem, which is already factored into the amount of Backstop Pool tokens displayed (see point 4).
6. The USD price of the Backstop Pool token.
7. The total number of LP tokens issued by the Swap Pool and your share of these tokens.
8. **Click the button** to execute the backstop redeem.

### Backstop Drain

A Backstop Drain of a Swap Pool is only possible if the [CR of the Swap Pool ](https://app.gitbook.com/o/axoDOM7fvGlVLdMc0tdk/s/JPteeI8zaYldKmZxPrYG/\~/changes/373/build/forex-amm/coverage-ratio-and-slippage)is above 100%.

To execute a Backstop Drain, navigate to [the Backstop Pool section](https://portal.pendulumchain.org/pendulum/nabla/backstop-pools) and click the "Withdraw" button. A popup will appear, displaying the following details:

<figure><img src="../../../.gitbook/assets/Screenshot 2024-10-21 at 04.58.16.png" alt=""><figcaption><p>Backstop Drain UI</p></figcaption></figure>

1. Select the respective Swap Pool from the drop-down menu. You can only select Swap Pools with a CR above 100%.
2. The number of Backstop Pool LP tokens you own, representing the maximum amount you can redeem.
3. Your current balance of Swap Pool tokens.
4. **Enter the amount** of LP tokens you wish to redeem.
5. The number of Swap Pool tokens you will receive based on the amount you redeem.
6. The total number of LP tokens issued by the Backstop Pool and your share of these tokens.
7. **Click the button** to execute the backstop drain.
