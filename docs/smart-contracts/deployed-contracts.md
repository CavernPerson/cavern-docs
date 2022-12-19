# Deployed Contracts

## Contract Addresses

The core smart contracts of Cavern are deployed on the [Terra blockchain](https://terra.money), and can be found at the below networks:

| Network Classification | Chain ID     | axlUSDC Address | 
| ---------------------- | ------------ | --------------- |
| Mainnet                | `phoenix-1` | TODO | 
| Testnet                | `pisco-1`  |  ibc/D70F005DE981F6EFFB3AD1DF85601258D1C01B9DEDC1F7C1B95C0993E83CF389 |

For money market and liquidations, a separate set of contracts are to be deployed for each Terra stablecoin denomination. Each set, called Markets, will use different Terra denominations as their base currency. Only axlUSDC-supporting contracts have been deployed on initial launch.

### aLUNA Smart Contracts

:::::{tab-set}
::::{tab-item} Mainnet
#### Core Contracts

| Contract            | Address                                                                                                                                    |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Hub                 | [terra1mtwph2juhj0rvjz7dy92gvl6xvukaxu8rfv8ts](https://finder.terra.money/columbus-4/address/terra1mtwph2juhj0rvjz7dy92gvl6xvukaxu8rfv8ts) |
| Reward              | [terra17yap3mhph35pcwvhza38c2lkj7gzywzy05h7l0](https://finder.terra.money/columbus-4/address/terra17yap3mhph35pcwvhza38c2lkj7gzywzy05h7l0) |
| Rewards Dispatcher  | [terra1q9cs4d4x67u6yvsaswecf0usp2rygdnmrflzfj](https://finder.terra.money/columbus-5/address/terra1q9cs4d4x67u6yvsaswecf0usp2rygdnmrflzfj) |
| Validators Registry | [terra16j67029v236npntxjatwena6kh7rgvkwdkw0tm](https://finder.terra.money/columbus-5/address/terra16j67029v236npntxjatwena6kh7rgvkwdkw0tm) |

#### Cw20-Compliant Token Contracts

| Contract             | Address                                                                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Bonded LUNA (bLUNA)  | [terra1kc87mu460fwkqte29rquh4hc20m54fxwtsx7gp](https://finder.terra.money/columbus-4/address/terra1kc87mu460fwkqte29rquh4hc20m54fxwtsx7gp) |
| Staked LUNA (stLUNA) | [terra1yg3j2s986nyp5z7r2lvt0hx3r0lnd7kwvwwtsc](https://finder.terra.money/columbus-5/address/terra1yg3j2s986nyp5z7r2lvt0hx3r0lnd7kwvwwtsc) |
::::

::::{tab-item} Testnet
#### Core Contracts

| Contract            | Address                                                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Hub                 | [terra1u28n7urqhnu2v7d4vs3x6z2yqmz0g5n7dx9lwrnynjxjchm2lv8s276kdn](https://finder.terra.money/testnet/address/terra1u28n7urqhnu2v7d4vs3x6z2yqmz0g5n7dx9lwrnynjxjchm2lv8s276kdn) |
| Reward              | [terra18e9c80ehqaee0963uqeaykapfef3v0a2xdm5uc28f44l9cv3tdeqyesm2e](https://finder.terra.money/testnet/address/terra18e9c80ehqaee0963uqeaykapfef3v0a2xdm5uc28f44l9cv3tdeqyesm2e) |
| Rewards Dispatcher  TODO| [terra1p6ecqfknww4dkehdfsc5u9kqe0x0rvss3j3q5c](https://finder.terra.money/testnet/address/terra1p6ecqfknww4dkehdfsc5u9kqe0x0rvss3j3q5c) |
| Validators Registry TODO | [terra10wt548y4y3xeqfrqsgqlqh424lll8fqxp6dyed](https://finder.terra.money/testnet/address/terra10wt548y4y3xeqfrqsgqlqh424lll8fqxp6dyed) |


#### Cw20-Compliant Token Contracts

| Contract             | Address                                                                                                                                 |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Bonded LUNA (aLUNA)  | [terra1qplftykc0sehm2632zd0n5swdxc3k24sjtsf9lm8em50fqyyt8aq2k6u26](https://finder.terra.money/testnet/address/terra1qplftykc0sehm2632zd0n5swdxc3k24sjtsf9lm8em50fqyyt8aq2k6u26) |

::::
:::::


### TerraUSD Market Smart Contracts

::: {danger}
### **WARNING**

Sending native tokens with a denomination not supported by the recipient contract will lead to **PERMANENT LOSS OF FUNDS**.
:::

Below are addresses of money market and liquidation contracts that use **axlUSDC** as their base denomination.

#### Money Market

:::::{tab-set}
::::{tab-item} Mainnet
#### Core Contracts

| Contract           | Address                                                                                                                                    |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Overseer           | [terra1tmnqgvg567ypvsvk6rwsga3srp7e3lg6u0elp8](https://finder.terra.money/columbus-4/address/terra1tmnqgvg567ypvsvk6rwsga3srp7e3lg6u0elp8) |
| Market             | [terra1sepfj7s0aeg5967uxnfk4thzlerrsktkpelm5s](https://finder.terra.money/columbus-4/address/terra1sepfj7s0aeg5967uxnfk4thzlerrsktkpelm5s) |
| bLuna Custody      | [terra1ptjp2vfjrwh0j0faj9r6katm640kgjxnwwq9kn](https://finder.terra.money/columbus-4/address/terra1ptjp2vfjrwh0j0faj9r6katm640kgjxnwwq9kn) |
| bETH Custody       | [terra10cxuzggyvvv44magvrh3thpdnk9cmlgk93gmx2](https://finder.terra.money/columbus-4/address/terra10cxuzggyvvv44magvrh3thpdnk9cmlgk93gmx2) |
| Interest Model     | [terra1kq8zzq5hufas9t0kjsjc62t2kucfnx8txf547n](https://finder.terra.money/columbus-4/address/terra1kq8zzq5hufas9t0kjsjc62t2kucfnx8txf547n) |
| Distribution Model | [terra14mufqpr5mevdfn92p4jchpkxp7xr46uyknqjwq](https://finder.terra.money/columbus-4/address/terra14mufqpr5mevdfn92p4jchpkxp7xr46uyknqjwq) |
| Oracle             | [terra1cgg6yef7qcdm070qftghfulaxmllgmvk77nc7t](https://finder.terra.money/columbus-4/address/terra1cgg6yef7qcdm070qftghfulaxmllgmvk77nc7t) |

#### Cw20-Compliant Token Contracts

| Contract               | Address                                                                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Cavern USDC (aUSDC) | [terra1hzh9vpxhsk8253se0vv5jj6etdvxu3nv8z07zu](https://finder.terra.money/columbus-4/address/terra1hzh9vpxhsk8253se0vv5jj6etdvxu3nv8z07zu) |
::::

::::{tab-item} Testnet
#### Core Contracts

| Contract           | Address                                                                                                                                 |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| Overseer           | [terra1qq3m9yn7h9gjgd6rs2t58qkjrqngl436sv6w3dak2svkc8lapx4qtxylsv](https://finder.terra.money/testnet/address/terra1qq3m9yn7h9gjgd6rs2t58qkjrqngl436sv6w3dak2svkc8lapx4qtxylsv) |
| Market             | [terra17xhgwkrk3pnlkkw0rdsv75qn0m0whgeaw4rd2muqmtgsdmgkutqqaa4a44](https://finder.terra.money/testnet/address/terra17xhgwkrk3pnlkkw0rdsv75qn0m0whgeaw4rd2muqmtgsdmgkutqqaa4a44) |
| bLuna Custody      | [terra1mv0mhsdzhkf20jpja28u9xfa27esmdgcgs6c6enzx3dru5mqpu4qua9007](https://finder.terra.money/testnet/address/terra1mv0mhsdzhkf20jpja28u9xfa27esmdgcgs6c6enzx3dru5mqpu4qua9007) |
| Interest Model     | [terra192p3z7wdqq0hgvgu23wkrkpeqwyp99nxrex78d3mrehdgu87gexq6aw2lu](https://finder.terra.money/testnet/address/terra192p3z7wdqq0hgvgu23wkrkpeqwyp99nxrex78d3mrehdgu87gexq6aw2lu) |
| Oracle             | [terra1z7483ujm8fdqmmdy8c2ncq9p5lf4rx2dca6dmsm2536mwvskvt6qjaqz4s](https://finder.terra.money/testnet/address/terra1z7483ujm8fdqmmdy8c2ncq9p5lf4rx2dca6dmsm2536mwvskvt6qjaqz4s) |

#### Cw20-Compliant Token Contracts

| Contract               | Address                                                                                                                                 |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Cavern Axelar USDC (aUSDC) | [terra1nn7dewwfnjqzy580uykvfp2fa3c8rmpu5dh7cmrptye0lgzsrh7q7mkeme](https://finder.terra.money/testnet/address/terra1nn7dewwfnjqzy580uykvfp2fa3c8rmpu5dh7cmrptye0lgzsrh7q7mkeme) |
::::
:::::

#### Liquidation Contract

:::::{tab-set}
::::{tab-item} Mainnet
#### Core Contracts

| Contract                       | Address                                                                                                                                    |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ 
| Liquidation Queue Contract     | [terra1e25zllgag7j9xsun3me4stnye2pcg66234je3u](https://finder.terra.money/columbus-5/address/terra1e25zllgag7j9xsun3me4stnye2pcg66234je3u) |
::::

::::{tab-item} Testnet
#### Core Contracts

| Contract                       | Address                                                                                                                                 |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| Liquidation Queue Contract     | [terra1jhydm6anuuweuzx2p6aq7j03qtehakwv0m4y9x9ce8jqcn3d2r4qw90w48](https://finder.terra.money/testnet/address/terra1jhydm6anuuweuzx2p6aq7j03qtehakwv0m4y9x9ce8jqcn3d2r4qw90w48) |
::::
:::::