# Collateral Attributes

The attributes of a whitelisted aAsset collateral is determined by its `Max LTV` parameter, defined as the maximum portion of collateral value that can be borrowed. This value signals aAsset's the level of usability as Cavern collateral, where aAssets that make poor collateral (e.g. low exchange liquidity, high price volatility) are assigned low `Max LTV` values and vice versa. For example, providing 100 UST worth of collaterals with a `Max LTV` of 50% enables the user to borrow up to 50 UST.


| Parameter Name | Description                                              |
| -------------- | -------------------------------------------------------- |
| `Max LTV`      | Maximum portion of collateral value that can be borrowed |

## Parameter Values

### Up-To-Date

| Collateral Ticker | Collateral Name | Parameter Name | Human-Readable Value | Raw Value (In Contract State) |
| ----------------- | --------------- | -------------- | -------------------- | ----------------------------- |
| **aLUNA**         | Bonded Luna     | `Max LTV`      | 60%                  | 0.6                           |

### At Protocol Genesis

| Collateral Ticker | Collateral Name | Parameter Name | Human-Readable Value | Raw Value (In Contract State) |
| ----------------- | --------------- | -------------- | -------------------- | ----------------------------- |
| **aLUNA**         | Bonded Luna     | `Max LTV`      | 60%                  | 0.6                           |
