# Borrower incentives

Calibration of the borrower incentives distribution rate is used to control stablecoin borrow demand, which in turn affects the stablecoin deposit rate. The distribution rate is adjusted based on the relation between the current deposit rate and the target deposit rate.

If the current deposit rate is calculated to be below the target, the borrower incentives distribution rate is increased by a factor of `Increment Multiplier`. Otherwise, if the current deposit rate is above the target, the distribution rate decreases by a factor of `Decrement Multiplier`.

To prevent the distribution rate from spiking and having an excessively high rate, the distribution rate is capped to the `Borrower Emission Cap`. The distribution rate also has a minimum rate of `Borrower Emission Floor` to allow a minimum baseline of block rewards incentives for borrowers.

Those parameters will in turn affect the state of the market contract and more precisely the `reserves_rate_used_for_borrowers` parameter every epoch.

| Parameter Name            | Value                                                             |
| ------------------------- | ----------------------------------------------------------------- |
| `Borrower Emission Cap`   | Maximum rate of staking rewards that are distributed to borrowers |
| `Borrower Emission Floor` | Minimum rate of staking rewards that are distributed to borrowers |
| `Increment Multiplier`    | Emission rate multiplier when increasing incentives distribution  |
| `Decrement Multiplier`    | Emission rate multiplier when decreasing incentives distribution  |

## Parameter Values

### Up-To-Date

| Parameter Name            | Human-Readable Value | Raw Value (In Contract State) |
| ------------------------- | -------------------- | ----------------------------- |
| `Borrower Emission Cap`   | 50% of block rewards | 0.5                           |
| `Borrower Emission Floor` | 5% of block rewards  | 0.05                          |
| `Increment Multiplier`    | 50% increment / week | 1.007266723782294841          |
| `Decrement Multiplier`    | 15% decrement / week | 0.997102083349256160          |

### At Protocol Genesis

| Parameter Name            | Human-Readable Value | Raw Value (In Contract State) |
| ------------------------- | -------------------- | ----------------------------- |
| `Borrower Emission Cap`   | 50% of block rewards | 0.5                           |
| `Borrower Emission Floor` | 5% of block rewards  | 0.05                          |
| `Increment Multiplier`    | 50% increment / week | 1.007266723782294841          |
| `Decrement Multiplier`    | 15% decrement / week | 0.997102083349256160          |