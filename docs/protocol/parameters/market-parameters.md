# Market Parameters

The mechanism behind Cavern's money market is controlled by a set of carefully determined parameters, which are `Target Deposit Rate`, `Threshold Deposit Rate`, `Buffer Distribution Factor`, `Max Borrow Factor`, and `Valid Price Timeframe`. 


Modifying the `Target Deposit Rate`, known as the Cavern Rate adjusts Cavern's target deposit APY, which the protocol attempts to achieve by constantly controlling the reserves distribution rate as borrower incentives.

The `Threshold Deposit Rate` value is the minimum deposit APY that Cavern tries to ensure by making direct deposit rate subsidizations from the yield reserve if the current deposit rate is observed to be below this value. Interest buffer usage from direct subsidization events are limited to a `Buffer Distribution Factor` portion of the yield reserve's balance per subsidization event.

In cases of excessive and uncontrollable borrow demand, the `Max Borrow Factor`, which limits the amount of stablecoin liquidity available to be borrowed, can be adjusted to allow aTerra redemptions to occur.

The money market is configured to be somewhat resilient to price oracle downtimes, where price values are considered invalid if they are older than `Valid Price Timeframe`.

| Parameter Name               | Description                                                                                       |
| ---------------------------- | ------------------------------------------------------------------------------------------------- |
| `Target Deposit Rate`        | The Cavern Rate. Target stablecoin deposit APY of Cavern Protocol                                 |
| `Threshold Deposit Rate`     | Threshold deposit APY to trigger yield reserve's interest buffer distribution                     |
| `Maximum Borrow Subsidy Rate`| Minimum borrow rate under which borrowers are not subsidized with the yield reserves              |
| `Buffer Distribution Factor` | Maximum portion of the yield reserve that can be distributed per deposit rate subsidization event |
| `Max Borrow Factor`          | Maximum portion of money market's stablecoin liquidity available for borrows                      |
| `Valid Price Timeframe`      | Time window before the money market considers oracle price data invalid                           |

## Parameter Values

### Up-To-Date

| Parameter Name               | Human-Readable Value | Raw Value (In Contract State)         |
| ---------------------------- | -------------------- | ------------------------------------- |
| `Target Deposit Rate`        | 10% APY              | 0.000000020466839100 (per-block rate) |
| `Threshold Deposit Rate`     | 9% APY               | 0.000000018505736100 (per-block rate) |
| `Maximum Borrow Subsidy Rate`| 10% APY              | 0.000000020466839100 (per-block rate) |
| `Buffer Distribution Factor` | 10%                  | 0.1                                   |
| `Max Borrow Factor`          | 95%                  | 0.95                                  |
| `Valid Price Timeframe`      | 60 seconds           | 60                                    |

### At Protocol Genesis

| Parameter Name               | Human-Readable Value | Raw Value (In Contract State)         |
| ---------------------------- | -------------------- | ------------------------------------- |
| `Target Deposit Rate`        | 10% APY              | 0.000000020466839100 (per-block rate) |
| `Threshold Deposit Rate`     | 9% APY               | 0.000000018505736100 (per-block rate) |
| `Maximum Borrow Subsidy Rate`| 10% APY              | 0.000000020466839100 (per-block rate) |
| `Buffer Distribution Factor` | 10%                  | 0.1                                   |
| `Max Borrow Factor`          | 95%                  | 0.95                                  |
| `Valid Price Timeframe`      | 60 seconds           | 60                                    |