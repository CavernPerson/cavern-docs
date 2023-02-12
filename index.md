# Home

You can access Cavern through the official [Web App](/docs/user-guide/webapp/README.md).

Welcome to the Cavern documentation site.

## What is Cavern?

**Cavern** is a decentralized savings protocol offering low-volatile yields on axlUSDC deposits on Terra. The Cavern rate is powered by a diversified stream of staking rewards from major proof-of-stake blockchains, and therefore can be expected to be much more stable than money market interest rates.  The Cavern community believes that a stable, reliable source of yield in Cavern has the opportunity to become the reference interest rate in crypto.

The Cavern protocol defines a money market between a **lender**, looking to earn stable yields on their stablecoins, and a **borrower**, looking to borrow stablecoins on stakeable assets. To borrow stablecoins, the borrower locks up [Bonded Assets](/docs/protocol/bonded-assets-bassets/README.md) (aAssets) as collateral, and borrows stablecoins below the protocol-defined borrowing ratio. The diversified stream of staking rewards accruing to the global pool of collateral then gets converted to stablecoin, and then conferred to the lender in the form of a stable yield.&#x20;

Deposited stablecoins are represented by [Cavern USDC (aUSDC)](./docs/protocol/money-market/README.md#usage). aUSDC tokens are redeemable for the initial deposit along with accrued interest, allowing interest collection to be done just by holding on to them. Cavern is structured to provide depositors with:

* **High, stable deposit yields** powered by rewards of [aAsset collaterals](./docs/protocol/money-market/README.md#algorithmic-interest-rate)
* **Instant withdrawals** through [pooled lending](./docs/protocol/money-market/README.md#depositing-stablecoins) of stablecoin deposits
* **Principal protection** via [liquidation](/docs/protocol/loan-liquidation.md) of loans in risk of undercollateralization

Cavern is an open, permissionless savings protocol, meaning that any third-party application is free to connect and earn interest without restrictions. Cavern doesn't support the [Earn](https://docs.anchorprotocol.com/anchor-2/developers-earn/anchor-earn-sdk), [js](https://docs.anchorprotocol.com/anchor-2/developers-terra/anchor.js) or [cli](https://docs.anchorprotocol.com/anchor-2/developers-terra/anchor-cli) libraries that were developped by Anchor. However, feel free to adapt them to interact with Anchor contracts without the WebApp. Support for those libraries and tools will be added in the future.

Further documentation of the Cavern Protocol is provided in the following pages.

## Sections

Learn more about Cavern Protocol, its core smart contracts, and Javascript SDK.

* Learn more about the [Protocol](/docs/protocol/overview.md).
* Read up on the [Anchor Protocol](https://anchorprotocol.com/docs/anchor-v1.1.pdf) and [bAssets](https://anchorprotocol.com/docs/The\_bAsset\_Protocol.pdf), that inspired Cavern's mecanisms.&#x20;
* Check out the [Smart Contracts](/docs/smart-contracts/deployed-contracts.md).

## Community

* [Telegram](https://t.me/cavernprotocolofficial)
* [Twitter](https://twitter.com/CavernProtocol)
* [Discord](https://discord.com/invite/Bzau2dW9fu)

```{toctree}
:hidden:
/docs/security
```

```{toctree}
:caption: Protocol
:hidden:
/docs/protocol/overview
/docs/protocol/bonded-assets-bassets/README
/docs/protocol/money-market/README
/docs/protocol/loan-liquidation
```

```{toctree}
:hidden:
```

```{toctree}
:caption: User Guide
:hidden:
/docs/user-guide/webapp/README
```

```{toctree}
:caption: Smart Contracts
:hidden:
/docs/smart-contracts/deployed-contracts
/docs/protocol/parameters/README
/docs/smart-contracts/bluna/README
/docs/smart-contracts/money-market/README
/docs/smart-contracts/liquidations/README
```

```{toctree}
:caption: External Resources
:hidden:
Anchor WebApp <https://app.anchorprotocol.com>
Anchor Protocol GitHub <https://github.com/Anchor-Protocol>

Cavern WebApp <https://cavernprotocol.com>
Cavern Protocol GitHub <https://github.com/Cavern-Protocol>

Terra Blockchain <https://docs.terra.money>
```