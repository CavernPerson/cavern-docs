# aLuna 


This page is still under construction...

This section describes provides a high-level overview of aLuna smart contracts.

Those contract were forked directly from Anchor Protocol, no radical change were brought to those contracts. As the product matures, more documentation will be made available on this page to allow everyone to understand how the platform works thoroughly.

In the meantime, we redirect you to the original Lido contracts, that Cavern Protocol used as a basis to build its lending market.


## Smart Contracts

| Contract                                                                            | Function                                                                                   |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| [Hub](https://docs.terra.lido.fi/contracts/hub)                                     | Central hub that manages underlying Luna delegation / undelegation                         |
| [Reward](https://docs.terra.lido.fi/contracts/reward)                               | Handles bLuna reward distribution                                                          |
| [Rewards Dispatcher](https://docs.terra.lido.fi/contracts/rewards\_dispatcher)      | Accumulates rewards of Hub's delegations and manages them                                  |
| [Validators Registry](https://docs.terra.lido.fi/contracts/validators\_registry)    | Stores the list of whitelisted validators                                                  |
| [Tokens: aLuna](https://docs.terra.lido.fi/contracts/stLuna\_and\_bLuna) | Modified CW20 token contract for handling token balances                                   |

```{toctree}
:hidden:
Hub <https://lidofinance.github.io/terra-docs/contracts/hub>
Reward <https://docs.terra.lido.fi/contracts/reward>
Rewards Dispatcher <https://docs.terra.lido.fi/contracts/rewards\_dispatcher>
Validators Registry <https://docs.terra.lido.fi/contracts/validators_registry>
Tokens: bLuna and stLuna <https://docs.terra.lido.fi/contracts/stLuna_and_bLuna>
```