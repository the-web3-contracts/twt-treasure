# 升级演示过程

## 使用的钱包地址
```
Successfully created new keypair.
Address:     0xd449306df27faB97ec0431F4558ab75966743983
Private key: 0xb857bcf6f3ee005a79eea257a4ab467a3488b5006fa4a9dbba7d54a9a41aafa5
```

## 部署合约
```
forge script ./script/TreasureManagerScript.s.sol:TreasureManagerScript --rpc-url https://bsc-testnet.bnbchain.org  --broadcast
```

- 部署结果

```
  treasureManagerImplementation===== 0x5e998237E062A12d2EF39F0010A08283f90E5be1
  treasureManager===== 0x8afBD8325bE38051f7822297a98b6f045f99640C
  treasureManagerProxyAdmin===== 0x4Cd55a8eeCE7DDbC14E3857c68d7361744534B23
```

升级前没有 getWithdrawAddress，调用报一下错误

```
cast call --rpc-url https://bsc-testnet.bnbchain.org 0x8afBD8325bE38051f7822297a98b6f045f99640C "getWithdrawAddress()(address)"
Error: server returned an error response: error code 3: execution reverted: 0x, data: "0x"

cast call --rpc-url https://bsc-testnet.bnbchain.org 0x8afBD8325bE38051f7822297a98b6f045f99640C "withdrawManager()(address)"
0x1804c8AB1F12E6bbf3894d4083f33e07309d1f38
```

## 升级合约

```
forge script ./script/TreasureManagerScript.s.sol:TreasureManagerScript --sig "upgradeContract()" --rpc-url https://bsc-testnet.bnbchain.org  --broadcast
```

```
cast call --rpc-url https://bsc-testnet.bnbchain.org 0x8afBD8325bE38051f7822297a98b6f045f99640C "getWithdrawAddress()(address)"
0x1804c8AB1F12E6bbf3894d4083f33e07309d1f38

cast call --rpc-url https://bsc-testnet.bnbchain.org 0x8afBD8325bE38051f7822297a98b6f045f99640C "withdrawManager()(address)"
0x1804c8AB1F12E6bbf3894d4083f33e07309d1f38
```

## 转钱之后

```
cast call --rpc-url https://bsc-testnet.bnbchain.org 0x8afBD8325bE38051f7822297a98b6f045f99640C "tokenBalances(address)(uint256)" 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE
```

- 给用户发奖励

```
cast send --rpc-url https://bsc-testnet.bnbchain.org --private-key 0xb857bcf6f3ee005a79eea257a4ab467a3488b5006fa4a9dbba7d54a9a41aafa5 0x8afBD8325bE38051f7822297a98b6f045f99640C "setTreasureManager(address)" 0xd449306df27faB97ec0431F4558ab75966743983
cast send --rpc-url https://bsc-testnet.bnbchain.org --private-key 0xb857bcf6f3ee005a79eea257a4ab467a3488b5006fa4a9dbba7d54a9a41aafa5 0x8afBD8325bE38051f7822297a98b6f045f99640C "grantRewards(address,address,uint256)" 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE 0xC51B88f46425eCb3670592072E67430BC2aA20ED 30000000000000000
```
