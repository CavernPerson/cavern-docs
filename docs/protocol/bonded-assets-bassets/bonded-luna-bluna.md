# Bonded Luna (aLuna)

:::{note}
The below documentation only focuses on the high-level contents of aLuna. For more details, please send us a message via Twitter or on-chain (TODO)!
:::

aLuna tokens are aAssets built for the Terra blockchain, their value backed by underlying Luna delegations. aLuna tokens follows full compliance with the [CW20 standard](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw20/README.md), having the potential to be integrated into a wide variety of decentralized finance applications.

:::{note}
aLuna tokens are used as collateral to borrow Terra stablecoins from Cavern. Learn more about creating loan positions [here](../money-market/README.md).
:::

## Concepts

### **aLuna Exchange Rate**

The aLuna exchange rate is the rate of conversion used when aLuna is minted or redeemed. Defined as the amount of bonded Luna per aLuna in existence, the value initially starts with 1, and decreases with slashing events.

$$
\text{aLunaExchangeRate} = \frac{\text{lunaBonded}} {\text{aLunaSupply}}
$$

#### Shared Slashing Risk

aLuna tokens equally share all losses from slashing events of whitelisted validators. Slashing events decrease the aLuna exchange rate, lowering the calculated value of a aLuna token.

The protocol applies a fee of **0.5%** to aLuna mints and burns whenever the exchange rate is below 1, targeting a gradual recovery to a one-to-one peg.

### Validator Whitelist

The aLuna contract keeps a whitelist of validators, only permitting delegations to those included in the whitelist. This is crucial since all aLuna tokens equally share slashing risks, and delegations to low-performing validators could negatively affect all holders.

:::{tip}
The list of whitelisted validators can be viewed [here](./validator-whitelist.md).
:::

#### Registration

Validators that have proven their operational capabilities are eligible for whitelisting via our Twitter. Track records such as uptime and community support are factors of consideration.

#### Deregistration

CavernPerson may deregister underperforming validators from the whitelist, disallowing aLuna minters from making new delegations to them. Following deregistration, the aLuna contract automatically redelegates existing delegations to a different, randomly selected validator.

The Terra blockchain permanently disables validator addresses that have double signed a block (i.e. tombstoned). Tombstoned validators are also deregistered, with their remaining delegations redelegated. The new address of the tombstoned validator can later be re-registered to the whitelist if necessary.

### Undelegation Batches

The aLuna contract processes Luna undelegations in batches, creating them in epochs of **3 days**. Whenever an undelegation is done, an entry storing its information is created:

* `batch_id`: incrementally-increasing unique identifier of the undelegation batch
* `amount`: total amount of fee deducted aLuna unbonded in this batch
* `time`: time of batch undelegation
* `applied_exchange_rate`: aLuna exchange rate at the time of undelegation
* `withdraw_rate`: rate applied when later withdrawing undelegated Luna from this batch
* `released`: indicator on whether the unbonding period is over for this batch

When a batch is undelegated, `applied_exchange_rate` is stored as the aLuna exchange rate at the time of undelegation, and `released` is stored as `false`.

Later when users withdraw undelegated Luna, the contract first checks for newly undelegated batches by comparing the current time with the `time` of recent batches. Batches that are older than 21 days are considered undelegated, and are marked by updating `released` as `true`.

The `withdraw_rate`, which determines the amount of Luna withdrawable per unbonded aLuna, is also updated to account for slashing events that happened during batch undelegation. The amount of slashed Luna, calculated by comparing the Luna amount initially undelegated and the Luna amount actually received, is deducted pro-rata from the newly undelegated batches by updating the corresponding `withdraw_rate` to the new decreased value.

## Usage

:::{important}
A peg recovery fee of **0.5%** is applied to aLuna minting and redeeming when the aLuna exchange rate is lower than 1.
:::

### Minting aLuna

:::{note}
Users don't have to specify a validator when minting aLuna, it will be chosen for them.
:::

aLuna tokens are minted by delegating Luna via the aLuna contract. Given a single delegation, the exact number of validators that will receive delegations and the amount that they will receive depends on the current distribution of stake.

The contract takes a sorted (ASC) list of validators, calculates the desired amount that each validator should have `target_stake = (total delegated + delegation_amount) / num_validators` and begins adding stake up to the desired amount, starting from the validator with the least stake. The exact amount of a single delegation is calculated as `target_stake - validator_stake`, and you'll have as many delegations as it takes to "drain" the `delegation_amount`.

:::{note}
Implementation of the stake distribution algorithm can be found [here](https://github.com/lidofinance/lido-terra-contracts/blob/main/contracts/lido\_terra\_validators\_registry/src/common.rs#L19).
:::

The amount of aLuna minted is dependent on the current aLuna exchange rate -- minted aLuna amounts will be greater than the Luna amount sent when the aLuna exchange rate is below 1.

### Redeeming aLuna

:::{warning}
Slashing occurrences between the time of request and withdrawal may affect the final amount later withdrawn.
:::

Any aLuna holder can redeem their tokens for their underlying bonded Luna. Redemption is a two-step process; 1) requesting to unbond aLuna (undelegates underlying Luna) and 2) withdrawing undelegated Luna.

Due to the Terra blockchain's unbonding period, a complete redemption cycle requires **at least 21 days** to finish.

#### Requesting to Unbond aLuna

A aLuna unbond request triggers the undelegation its underlying staked Luna. To track the Luna amount later withdrawable by each user, a waitlist entry with the the below information is created:

* `address`: address of aLuna unbond requester
* `batch_id`: ID of the batch that includes the user's undelegation request
* `amount`: amount of fee deducted aLuna unbonded by user

The user's request is added to the current [undelegation batch](bonded-luna-bluna.md#undelegation-batches), which is undelegated in epochs of **3 days**. If 3 days have past since the previous batch was undelegated, the current batch, along with the user's request is undelegated.

To disallow any holder from manipulating the aLuna contract's delegations by constant minting and redeeming, undelegations are performed from a randomly selected validator.

#### Withdrawing Undelegated Luna

Users that previously made a request to unbond aLuna can later withdraw the undelegated Luna tokens. The amount of Luna that the user can withdraw from an undelegation batch is calculated by multiplying the amount in the user's waitlist with the batch's `withdraw_rate`. Summation of this value for batches that are past the unbonding period (`released` marked as `true`) yields the user's total withdrawable amount.

### aLuna Rewards

aLuna tokens accrue **TerraUSD** rewards, generated from delegation rewards of underlying Luna delegations. Delegation rewards, collected in various native token denominations (TerraUSD, TerraSDR, Luna, etc.), are swapped for TerraUSD. Swapped TerraUSD is then distributed pro-rata to aLuna holders.

#### Claiming Rewards

Holders can send a request to the aLuna contract, which prompts the transfer of accrued rewards to their account. As rewards accrue during the user's period of ownership, transferring aLuna to a different user automatically credits accrued rewards to the previous holder.

## Fees

### Peg recovery fee

Slashing events decrease the aLuna exchange rate, lowering the calculated value of a aLuna token. The protocol applies a fee of 0.5% (configurable value) to aLuna mints and burns whenever the exchange rate is below 1, targeting a gradual recovery to a one-to-one peg.

### Lido operating costs fee

All accrued aLuna rewards are taxed at a configurable % rate. This fee is initially set as **0%**, but may increase with the involvement of Lido's governance DAO.
