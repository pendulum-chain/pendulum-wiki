# Security and Audits

The Forex AMM consists of various sets of smart contracts. These smart contracts are implemented in Solidity and are by default not compatible with Polkadot runtimes. However, the Pendulum team implemented a compatibility layer to facilitate the deployment of Solidity-based smart contracts on Pendulum.  This layer consists of wrapper smart contracts and [ink! chain extensions](https://use.ink/3.x/macros-attributes/chain-extension/) to make smart contracts able to access price and asset information stored in the runtime.&#x20;

**These wrapper smart contracts and chain extensions were audited by Hacken.**&#x20;

**Detailed report** -> [https://audits.hacken.io/pendulum/](https://audits.hacken.io/pendulum/).&#x20;

A blog post explaining how these smart contracts interact with each other can be found [here](https://medium.com/pendulum-chain/solidity-smart-contracts-on-polkadot-b49a648284ec).&#x20;

