# Overview

## Too Long; Did Not Read (TL;DR)

Using LUNA staking yields and money markets, the Cavern Protocol composes a fully decentralized fixed income instrument.&#x20;

1. **<strike>Governance</strike>** A centralized entity (for now) sets the **“Cavern Rate”**. The “Cavern Rate” is the target APY Cavern seeks to pay out to depositors. Cavern Protocol doesn't believe the protocol is mature enough to let its parameters be controlled by governance. The rate is fixed and will be changed when needed.
2. **Staking rewards make up the “real yield”** … underneath the hood, Cavern implements the classical money market, with the caveat that whitelisted collateral is reserved for liquid staking derivatives of major PoS protocols (I limited that to Luna for now). The collateral earns staking rewards, making up the real yield.&#x20;
3. **The "real yield" is stabilized around the "Cavern Rate"**  … reserves and borrowing incentives help the real yield to converge to the Cavern Rate.&#x20;
   1. If real yield > Cavern Rate, the excess yield is stored in a UST denominated “yield reserve”. Staking incentives to borrowers drop by 15% every week.&#x20;
   2. If real yield < Cavern Rate, the yield shortfall is drawn down from the yield reserve until it is depleted. Additionally, borrowers incentives increase by 50% every week until the real yield converges to the Cavern Rate, or until the reserves or completely depleted.

4. This protocol is deeply inspired from **Anchor Protocol** (most of the codes used was forked), that operated on Terra Classic. The Terra crash happened partially because the protocol incentivized depositors and borrowers using expendable cash AND because stabilisation of the rate came from speculative tools, such as unorganic Utility Token incentives. Cavern wants to restart the Anchor model, we believe it to be beneficial to the ecosystem. However, we need reduce the risk inherent to these kind of money markets and that's exactly what Cavern Protocol wants to work towards. Again, this protocol is not risk-free but our main focus and aim is and will always be stability for its users.


## Components

Cavern Protocol can be subdivided to the below components:

| Component                                                        | Description                                                                                |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| [Bonded Assets (aAssets)](bonded-assets-bassets/README.md)                | Tokenized representations of bonded PoS assets                                             |
| [Money Market](money-market/README.md)                                    | Handles lending and borrowing of Terra stablecoins, with borrows collateralized by aAssets |
| [Liquidation Contract](./loan-liquidation.md)                      | Manages collateral liquidations of loans at risk of undercollateralization                 |

## Protocol Participants

Four types of users exist in the Cavern ecosystem: **depositors** (lenders), **borrowers**, **liquidators**, and **liquidation triggers**<strike>, and **ANC liquidity providers**</strike>. Cavern also requires **oracle feeders**, critical for providing the necessary infrastructure.

In Cavern Protocol, depositors are incentivized to lend Terra stablecoins to Cavern's money market, which is borrowed out by borrowers through aAsset collateralized loans. Interest paid by borrowers are given to depositors, along with subsidies generated from rewards of deposited aAsset collaterals. In addition, the protocol prevents borrowers from forming liabilities in excess of collateral value by incentivizing liquidators to observe and liquidate loans at risk of undercollateralization.



### Depositor (Lender)

A **Depositor** is a user that lends stablecoins (axlUSDC) to the Cavern money market. Deposited stablecoins are pooled and lent out to borrowers, with accrued interest pro-rata distributed to all depositors.

Depositors receive newly minted [Cavern Terra (aTerra)](./money-market/README.md#usage) in exchange for their deposit. aTerra tokens represent a depositor's share in the stablecoin pool and can later be redeemed to claim the initial stablecoin deposit, along with accrued interest and depositor subsidies.



### Borrower

**Borrowers** are entities that create aAsset-collateralized loan positions to borrow Terra stablecoins from the Cavern money market. aAssets that were whitelisted by Cavern can be deposited and locked to create a loan position. Positions are required to maintain a [loan-to-value (LTV)](./money-market/README.md#borrowing-terra-stablecoins) ratio below the set maximum.

By borrowing, users can gain access to liquidity without losing price exposure to their aAsset collateral. Borrowers are recommended to keep a close eye on their loan position's LTV ratio, as loans with LTV ratios over the set maximum are subject to liquidation.


### Liquidator

A **Liquidator** submits a bid to the Liquidation Queue Contract, offering to purchase the liquidated collateral in exchange for the liquidator's Terra stablecoins. In doing so, they choose a premium at which their bid should be executed. The lower the bid, the more priority the liquidator has in the queue resulting in an earlier bid execution. However, a smaller bid means a smaller profit when liquidation occurs and a greater to risk to get the collaterals at a low price.

Collaterals are liquidated by executing bids in the Liquidation Contract. Only bids that were submitted by the liquidator can be executed; the liquidator triggering liquidations must have a pre-existing bid submitted by them. On execution, the liquidator receives the collateral tokens at a discounted rate, and stablecoins in the liquidator's bid is used to repay the liquidated borrower's loan.

### Liquidation triggers

A **Liquidation trigger** monitors for the existence of risky loans (loans with an LTV ratio above the set maximum) and requests loan collaterals to be liquidated if necessary.

Collaterals are liquidated by executing bids in the Liquidation Queue Contract. On execution, the liquidator receives the collateral tokens at a discounted rate, and stablecoins in the liquidator's bid is used to repay the liquidated borrower's loan. The liquidation trigger gets a small cut of the liquidated collaterals in return for their effort.


### <strike>ANC Liquidity Provider</strike>

<strike>**ANC Liquidity Providers** are entities that provide liquidity to the ANC-UST Terraswap Pair. They manage the initial bootstrapping of the exchange liquidity between ANC tokens and UST. ANC exchange liquidity is critical as ANC tokens are distributed as borrower incentives, used to calibrate the stablecoin deposit rate.</strike>


### Oracle Feeder

An **Oracle Feeder** is a Terra account that is responsible for providing an accurate and up-to-date price feed for aAsset collaterals. Fed-in price data is used to calculate the collateral value of a borrower, also used as the reference price in the Liquidation Contract.

As an entity crucial for protocol operation, Cavern's oracle feeder is initially set as the creator of Cavern Protocol. <strike>Through governance</strike> In the future, support can be extended to third-party oracle feeders as the protocol further matures.

## Tokens

| Name                                                       | Type               | Function                                |
| ---------------------------------------------------------- | ------------------ | --------------------------------------- |
| Axelar USDC (axlUSDC)                                      | IBC Token          | Stablecoin                              |
| [Bonded Assets (aAssets)](./bonded-assets-bassets/README.md)          | Cw20 Token         | Loan collateral for Cavern money market |
| [Cavern Terra (aTerra)](./money-market/README.md#usage) | Cw20 Token         | Deposit receipt for Cavern money market |
