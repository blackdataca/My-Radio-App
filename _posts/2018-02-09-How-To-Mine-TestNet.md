---
layout: post
title: How to Mine Testnet Coins
---

[achievecoin.org](http://achievecoin.org)

To mine AchieveCoin in testnet​, you can join a testnet pool. Please be aware that all the coins mined in testnet have​ ​zero​ ​value​, so miners can just view this as an end-to-end functional test for mining setup.

# Download AchieveCoin Core
AchieveCoin Core  includes a transaction verification engine and connects to the AchieveCoin network as a full node. Moreover, a cryptocurrency wallet, which can be used to transfer funds, is included by default.

You can compile AchieveCoin Core from source code,

or

download pre-compiled AchieveCoin Core from [Github](https://github.com/achievecoin/AchieveCoin/releases).
```
If you are running Windows, download AchieveCoin.Core.Win.x.x.x.zip.
If you are running Linux, Ubuntu, download AchieveCoin.Core.Linux.x.x.x.tar.gz.
If you are running Mac OS, download AchieveCoin.Core.Mac.x.x.x.zip
```
Unpack executable files from downloaded package into a convenience folder. There is no installation needed.

# Running AchieveCoin Core
Similar to Bitcoin, you may want to create an achievecoin.conf file in datadir folder (optional).
The default datadir folder location is here
```
Windows: C:\Documents and Settings\<username>\Application Data\achievecoin
Win10: C:\Users\<username>\AppData\Roaming\achievecoin
Mac: ~/Library/Application Support/achievecoin
Linux: ~/.achievecoin
```

Add the following line in achievecoin.conf file (optional)
```
testnet=1
```

Start AchieveCoin Core by Running
```
./ach-qt -testnet (on Linux and Mac)
ach-qt.exe -testnet (on Windows)
```

# Creating Testnet Address
On AchieveCoin Core, go to File menu, select Receiving addresses..., then click New button. For privacy concerns, it is recommended to create new address for each transaction.
Testnet address starts with lower-case letter 'a'.


# Mining Pools and Mining Software
[http://minelab.space](http://minelab.space) is a reference implementation of AchieveCoin pool. You can find modified pool and miner software at the public repository: [https://github.com/achievecoin/z-nomp-achievecoin](https://github.com/achievecoin/z-nomp-achievecoin)


Popular Mining Software

[EWBF miner - nVidia GPU](https://github.com/poolgold/ewbf-miner-btg-edition/releases)

[Claymores ZEC/BTG miner - Radeon RX GPU](https://github.com/poolgold/ClaymoreBTGMiner/releases)


# CPU Mining
Although GPU is much much more effective than CPU for calculating hash, it is still possible to generate coins using CPU when network difficulty is low. The AchieveCoin Core has a built-in unoptimized mining command. Under Help -> Debug Window -> Console -> enter

```
generate 1
```

Parameter 1 stands for 1 block (50 coins).

To learn more

```
help generate
```

# Pool​ ​adoption
Because of the PoW change, all the Bitcoin pools are incompatible with AchieveCoin. Bitcoin Gold pools can be use with just configuration change. Zcash pools can be used with some tweaks.

Significant changes for integration
* The block header format is mostly compatible with Zcash except:
  * `nVersion` is not 4. Instead it’s defined by BIP9.
  * The first 4 bytes of `hashReserved` (32 lows bits) are used to store the block height.
* Other than the block height, the block format is the same as Bitcoin.
* No per-block founder rewards.
* Block subsidy and block interval is the same as Bitcoin rather than Zcash.
* Address format (AchieveCoin testnet address starts with letter 'a')

# Wallet​ ​adoption
Significant changes for integration
* P2P network changes: protocol version, network magic, block header format
* Consensus changes: PoW
* SIGHASH_FORK_ID replay protection: The way to sign a transaction is changed because of the
replay protection. (Will be changed to full BIP143 style SIGHASH for the next testnet reset for enhance hardware wallets experience.)
* Sign message magic: changed to “AchieveCoin Signed Message:\n”
* Compact block feature has been disabled temporarily.
* Address format (AchieveCoin testnet address starts with letter 'a')


Happy Mining!

AchieveCoin Team
