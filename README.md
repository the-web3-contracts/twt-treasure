

```shell
forge verify-contract --rpc-url $RPC_URL --verifier etherscan --verifier-url 'https://explorer.roothashpay.com/api/' 0xC10F6186Bb3C9E68516D0e2F829f1b95C323d542 ./src/TreasureManager.sol:TreasureManager
```
- 部署合约的地址
```shell
treasureManagerImplementation===== 0xA93983586Ea6527A485E9C572C8a5e139b7049Ce
treasureManager===== 0x7111cfFF8887E90596fdC2e4c7d6128E1D03fC53
treasureManagerProxyAdmin===== 0x22E8A434D5F420CE6e5a4389219cfD8B13E0D060
```


```shell
forge verify-contract --rpc-url $RPC_URL --verifier etherscan --verifier-url 'https://api.etherscan.io/v2/api/' 0x7111cfFF8887E90596fdC2e4c7d6128E1D03fC53 ./src/TreasureManager.sol:TreasureManager
```

```shell
1Q4393KI12224CM53G4FPAP4GJVGY8VF6S
```

```shell
'https://api.etherscan.io/v2/api?apikey=YourApiKeyToken
```
