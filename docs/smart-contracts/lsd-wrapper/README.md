# LSD Collaterals

This section provides a high level overview of the LSD wrapper system Cavern Protocol uses to accept Liquid Staking Derivatives (LSD) as collateral.


# Introduction

As the Cosmos and Terra ecosystem evolves, it becomes clear that the 21 days locking period for staked tokens is very difficult to navigate for more agile users. LSDs are one solution to that issue and present and very good way to stake user's tokens while preserving the freedom to exit their positions easily. It is natural that a money market such as Cavern Protocol integrates them as collaterals to allow users to borrow freely. Moreover with very low pool liquidity, aLuna is difficult to use because borrowers can't exit their positions quickly.

# Integrating LSDs in the protocol

As explained in the [a-Asset page](../../protocol/bonded-assets-bassets/README), an asset needs to fulfill multiple criteria in order to be accepted as collateral : 
1. Fungibility
2. Default 1:1 Conversion
3. Ease of Redemption
4. Reward Accruing

A quick remark here, aLuna unfortunately doesn't really fit the third criteria and this will be abandoned very quickly.

An LSD is indeed Fungible, has an ease of redemption and accrues rewards constantly. However LSDS don't have a default 1:1 conversion and their exchange rate changes with time (the tokens doesn't rebase but rather increases in value).

Thus, Cavern Protocol will never be able to integrate raw LSDs as collaterals. However and this will be the topic of the next section, Cavern Protocol was able to develop an LSD interface, so that users can deposit LDSs in the platform and borrow against the underlying value of those LSDs. LSDs are not exactly accepted as collaterals but rather allow the users to borrow against the value of the LSD at the time of deposit. Let's dig a little deeper.

# Turn LSDs in to $1:1$ convertible assets

In order to add the point n°3 to our collateral, we see two solutions : 
1. Make a wrapper token around the LSD that rebases instead of increasing in price. This way, the wrapper will always be convertible $1:1$ with the underlying token by essence. However, this technique alone will remove the reward accruing part of the LSD.
2. Make a wrapper token around the LSD from which we extract all the generated staking yield (this is actually equivalent to rebasing and removing the extra underlying value collected since the last rebase). This way, the wrapper token is always convertible $1:1$ with the underlying asset and we keep the staking rewards to operate the protocol


# Implementation details

In order to achieve this conversion from an LSD to an acceptable collateral token on Cavern Protocol, we use a wrapper token contract, that connects to the whole money market in the same way as the [aLuna contract](../bluna/README). It has a hub contract, a rewards contract as well as a custody contract. Those are very similar to the aLuna ones. With the exception that instead of withdrawing rewards from validators at each epoch, the system will do 3 things sequentially : 

1. Query the amount of LSD tokens stored in the wrapper contract. Get the value of those tokens in underlying token units.
2. 
	a. If the value in underlying token units is *lower* than the number of minted tokens, this means that the LSD suffered a Slashing event and the overseer contract does nothing. The oracle contract however will notice that and the collateral's price will suffer from it.  
	b. If the value in underlying token units is greater than the number of minted tokens, the contract will compute the LSD surplus and send them to the rewards contract responsible of distributing those rewards to the rest of the money market.
3. The rewards contractSwap the LSD surplus to the reward denomination (axlUSDC in our case) and distribute that to the money market itself.
	
Notice that in this mechanism, there is no need for keeping track of the rewards of all users, because the only users that will deposit collateral on the platform, use it to borrow and therefore pay the staking price directly to the overseer contract.  

# Analysis and remarks

With this mechanism, you may notice that what borrowers actually deposit is not the LSD but rather the underlying token. Indeed, the value of the collateral in underlying token units will stay the same when providing LSDs as collateral, but that means that the LSD value will get smaller with time. Let's take an example.
- Alice deposits $5$ ampLuna on Cavern. For simplification, let's say the exchange rate ampLuna - Luna is $1$ in the beginning of this scenario. It means Alice deposited $5$ Luna on Cavern Protocol.

- This ampLuna gets wrapped in a our wrapper token and used to borrow $4$ axlUSDC against it.

- A month later, Alice repays the loan and wants to withdraw her collateral. But now the exchange rate ampLuna - Luna is $1.05$, ampLuna's value raised $5$% from staking rewards. Alice will still get $5$ Luna worth of ampLuna back ~ $4.76$ ampLuna.

--> You see that Alice exchanged her LSD yield against the right to borrow a stable asset. 

The Cavern Protocol App doesn't display the tokens as wrapped for sake of simplicity but the mechanism involves a wrapped token and this yield extraction mechanism. 