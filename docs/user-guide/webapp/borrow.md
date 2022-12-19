# BORROW

The **BORROW** page can be used to borrow axlUSDC from Cavern. The protocol requires users to provide aAsset tokens as collateral before making a loan. To create aAssets from your staking tokens, see  the [BOND page guide](./bond.md).&#x20;

Borrows can be made until the loan's borrowing usage reaches the borrowing limit, calculated based on collateral types, their prices, and deposit amount. Loans with a borrowing usage higher than the borrowing limit can be liquidated, and thus it is important for borrowers to closely maintain their borrowing usage as changes in collateral prices may occur.

::: {note}
As of November 30th, 2022, Cavern only supports axlUSDC as the base currency.
:::

The **BORROW** page displays:

* **Collateral Value**: Total USD-denominated value of all collaterals provided by user.

* **Borrowed Value**: Total USD-denominated value of Terra stablecoins borrowed by user.
  *   **Borrowed**: Total amount of axlUSDC borrowed by user.


* **Net APY**: Net annualized percentage yield (APY) on borrows from both Borrow APR and Distribution APY
  * **Borrow APR**: Current annualized percentage rate (APR) of borrow interest.
  * **Distribution APY**: Current APY of reserves distributions to borrowers.

* **Loan Position Graph**: Displays the [risk ratio](../../protocol/loan-liquidation.md#collateral-liquidation) of user's loan position.
  * **Borrow Limit**: Maximum USD value borrowable by user based on provided collaterals.
  * **Borrowed Value / Borrow Limit Ratio**: Ratio value that signals user loan position's liquidation riskiness. Calculated by dividing user's borrowed value with their borrow limit.

## Providing aAsset collateral

::: {note}
Users should first obtain aAsset tokens in order to utilize them as loan collateral. aAsset minting can be done at the [**BOND**](bond.md) page in Cavern WebApp.
:::

1\. Navigate to the **BORROW** page.

![](../../assets/Provide-Collateral-1.png)

2\. Decide a aAsset collateral to deposit and click **\[Provide]**.

![](../../assets/Provide-Collateral-2.png)

3\. Enter the amount of collateral to provide. If the user already has a loan position, the provide amount can also be specified by selecting the loan's target borrow usage ratio via the slider bar. Click the **\[Proceed]** button to confirm.

![](../../assets/Provide-Collateral-3.png)

4\. Station Extension should prompt you to sign a transaction that contains the collateral provide operation. Confirm the details presented and enter your password to sign.

![](../../assets/Provide-Collateral-4.png)

5\. Collateral provide complete.

![](../../assets/Provide-Collateral-5.png)

## Borrowing Terra stablecoins

1\. Navigate to the **BORROW** page. Then, click **\[Borrow]**.

![](../../assets/Borrow-1.png)

2\. Enter the amount of stablecoins to borrow. The borrow can also be specified by selecting the loan's borrow usage via the slider bar, up until the borrow limit. Click the **\[Proceed]** button to confirm.&#x20;

![](../../assets/Borrow-2.png)

3\. Station Extension should prompt you to sign a transaction that contains the borrow operation. Confirm the details presented and enter your password to sign.

![](../../assets/Borrow-2.png)

4\. Borrow complete.

![](../../assets/Borrow-4.png)

## Repaying borrowed Terra stablecoins

1\. Navigate to the **BORROW** page. Then, click **\[Repay]**.
![](../../assets/Repay-1.png)

2\. Enter the amount of stablecoins to repay. The repay amount can also be specified by selecting the loan's borrow usage ratio via the slider bar, up until the current borrow usage amount. Click the **\[Proceed]** button to confirm.

![](../../assets/Repay-2.png)

3\. Station Extension should prompt you to sign a transaction that contains the repay operation. Confirm the details presented and enter your password to sign.

![](../../assets/Repay-3.png)

4\. Repay complete.

![](../../assets/Repay-4.png)

## Withdrawing aAsset collateral

::: {note}
Withdrawn aAsset collaterals can be redeemed for their underlying assets at the Cavern WebApp's [**BOND**](bond.md) page.
:::

1\. Navigate to the **BORROW** page.

![](../../assets/Withdraw-Collateral-1.png)

2\. Decide a aAsset collateral to withdraw and click **\[Withdraw]**.

![](../../assets/Withdraw-Collateral-2.png)

3\. Enter the amount of collateral to withdraw. The withdraw amount can also be specified by selecting the loan's borrow usage ratio via the slider bar. Click the **\[Proceed]** button to confirm.

![](../../assets/Withdraw-Collateral-3.png)

4\. Station Extension should prompt you to sign a transaction that contains the collateral withdraw operation. Confirm the details presented and enter your password to sign.

![](../../assets/Withdraw-Collateral-4.png)

5\. Collateral withdraw complete.

![](../../assets/Withdraw-Collateral-5.png)
