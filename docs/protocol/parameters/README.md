# Cavern Governance

Development and maturization of Cavern Protocol is not over yet, and we don't trust our product and mecanisms enough to be governed through decentralized on-chain governance. We are still at the beginning of Cavern's history and we need to be able to act quickly and in a coordinated fashion to correct mistakes or adjust parameters. In test mode, only 1 address had the access and modification priviledges. We will shortly move this dangerous state of things to a multisig of 5 people, a safer alternative to a single point of failure. We hope that control will be handed to the community very shortly so that decentralization can prevail. 

## Cavern Governance Token 

The protocol doesn't have any governance or utility tokens, because they are usually the source of speculation and work just like public companies, the share-holders don't have the interest of users at heart but rather their own. 

As stated above, the protocol doesn't have a decentralized governance for now, but we hope that in the future, the governance will be driven by usage (aUSDC ownership, bLuna ownership, borrowing LTV) and not by a utility token that could be disconnected from what the platform really is : a staking rewards subsidized lending market.

## Parameter Types

The protocol doesn't have a decentralized governance. However, those docs still regroup all the parameters used by the protocol, as part of our will and initiative to make information freely accessible and empower our users. Those parameters are organized in the same way Anchor Polls were, in order to keep a certain logic.


| Parameter Type                                                         | Description                                                                                         |
| ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [Collateral Attributes](collateral-parameters.md)   | Max LTV of a whitelisted collateral                                      |
| [Market Parameters](market-parameters.md)           | Parameter set in the Cavern money market                                                |
| [Liquidation Parameters](liquidation-parameters.md) | Parameter set in Cavern's [Liquidation Contract](../loan-liquidation.md)            |
| [Borrow Interest](interest-model.md)            | Parameters set in the stablecoin [borrow interest formula](../money-market/README.md#borrow-rate-model) |
| [Borrower incentives distribution](distribution-model.md)       | Parameters related to borrower incentives distribution                                            |
                                                                             |

```{toctree}
:hidden:
collateral-parameters
market-parameters
liquidation-parameters
interest-model
distribution-model
```