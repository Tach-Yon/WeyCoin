
WeyCoin 1.14.5.0 Release Notes: First Release
==========================================

###### Version: 1.14.5.0 (Initial)
###### Block Size (non-SegWit): 4 MB
###### Max Block Size Serialized Size: 16 MB
###### Proof-of-Work Algorithm: Lyra2rev2
###### Block Time: ~60 seconds
###### Coin Maturity: 100 blocks
###### Transactions Per Second: 133 (Bitcoin: 3, Bitcoin Cash: 27, Dash: 13)
###### Transactions Per 24 hours: 11,520,000
###### Difficulty Retargeting: New D106 Algorithm
###### Maxmium Coin Supply: 150 Million 
###### Treasury Funding: 5% Per Block
###### SegWit: Active
###### SegWit2x: Active
###### SegWit4x: Active
###### Lightning Network: Compatible
###### Atomic Swaps: Compatible
###### Masternodes: Enabled
###### Masternodes Collateral: 15,000 WAE
###### Masternode Reward: Rebalancing via New Reactive Equilibria (REV1) Algorithm
###### ZSMR: Explicit Masternode Decentralisation Promotion [Zero Reward to Block 50400]
###### ZSIP: Zero Start Instamine Protection [7 Days: 10080 Blocks]


__________________________________________________________________________


### Specifications

As above summary, in addition, the following notable items:


#### Coinbase Transactions, Pool Mining and Wallet Mining 

**IMPORTANT**

Due to the unique combination of SegWit, treasury reward, miner reward and Masternode payments, as of this writing, mining software and pools do not yet support WEYCOIN' coinbasetxn configuration.  The only way to mine at the moment is via WEYCOIN' wallet, as follows:

```
Approach 1 (Local):
(1) Start weycoind/weycoin-qt locally
(2) Run: "./weycoin-cli generate 1" (or via debug console in the Qt gui wallet)
```
```
Approach 2 (Remote):
(1) Start weycoind on remote server and local server
(2) On your local wallet (server) run: "./weycoin-cli getaccountaddress 0"
(3) On Your remote server Run: "./weycoin-cli generatetoaddress 1 <address from step2>"
(4) Shutdown local wallet (server)
```
We find ourselves in an attractive position of having a low barrier to entry at launch, which allows anyone and everyone to start mining from the outset.  You are only limited by the number of wallets that can be run simultaneously.  The latter is comparatively cheaper than setting up a multi-gpu mining rig.

We are curently working with mining pools to ensure that we can enable GPU/CPU pool mining as soon as practicable.


#### Zero Start Instamine Protection (ZSIP)

WEYCOIN blockchain has been set to issue a 0 block subsidy up to **block height 10080**.  At 1440 blocks per day, this is approximately 7 days. During this time, community members will be informed of launch and will be able to configure their setups for mining.  During this period there are no Treasury payments, either.


#### Maximum Coin Supply and Block Reward

WEYCOIN will be capped at a maxium supply of **150 million coins**.  This target supports a managed inflation rate that allows for a constant block reward of **10 WAEs**.

The constant block reward prevents event cliffs related to expected "halvings" and will support a more consistent and stable participation rate over a long time horizon.

More information will be available on the WEYCOIN' [website](http://weycoinproject.org)

##### The Monetary Curve Based on a 10 WAE Block Reward
![Alt text](mcurve.png)


##### The Monetary Curve Underlying Dataset with Zero Start Block Offset
![Alt text](monetary_curve_table.png)


#### POW Algorithm: Lyra2REv2

Fast, power-efficient and asic resistant algorithm.  The WEYCOIN development team will continue to support a decentralized asic resistant blockchain, and will update the POW algorithm if the latter is no longer the case.

The difference between Lyra2RE and Lyra2REv2 is as follows;

- Addition of 2 rounds of CubeHash (https://en.wikipedia.org/wiki/CubeHash) 
- Addition of 1 round of Blue Midnight Wish (https://www.mathematik.hu-berlin.de/~schliebn/dl/Blue-Midnight-Wish.pdf)
- Removal of Groestl (http://www.groestl.info/)

More specific information about Lyra2 itself can be obtained from: http://lyra-2.net/


#### **NEW** Difficulty Retargeting Algorithm (D106 - Amaury Sechet)

Recent public discussions on how to address Bitcoin Cash's hash rate oscillation has resulted in an excellent approach that addresses many weaknesses of various other algorithms.  A well developed analsysis was presented by Bitcoin Cash's developer Amaury Sechet and supported by Zawy12 via thorough analysis, with simulated results that demonstate the algorthim's effectiveness.  The proposed implementation was modified specific to WEYCOIN blockchain.

More information can be found here:

- [Bitcoin Mailing List Discussion](https://lists.linuxfoundation.org/pipermail/bitcoin-ml/2017-August/000136.html)
- [Bitcoin News - Bitcoin Cash Hard Fork](https://news.bitcoin.com/bitcoin-cash-hard-fork-plans-updated-new-difficulty-adjustment-algorithm-chosen/)
- [Karbowanec Difficulty Discussion](https://github.com/seredat/karbowanec/commit/231db5270acb2e673a641a1800be910ce345668a#commitcomment-22615466)

##### The Modified D106 Algorithm Targeting a 60 Second Block Time for WEYCOIN Blockchain
![Alt text](D106_algorithm_test.png)


#### Treasury Funding

In order to support continued development, exchange lisiting fees, web/node hosting costs, and various other operational costs related to running a successful blockchain, the WEYCOIN development team have decided to introduce a 5% treasury fee in perpetuity. We intend to ensure that the new currency is competitive and successful. To be able to deliver on that vision, we need to ensure that the currency is well-funded throughout its lifecycle. 

At 5%, approximately 72 blocks per day are mined for treasury (720 WAE).  In the spirit
of transparency, the following 2-of-3 multisig addresses are the official
treasury addresses:

```
[0] 3K3bPrW5h7DYEMp2RcXawTCXajcm4ZU9Zh
[1] 33Ssxmn3ehVMgyxgegXhpLGSBpubPjLZQ6
[2] 3HFPNAjesiBY5sSVUmuBFnMEGut69R49ca
[3] 37jLjjfUXQU4bdqVzvpUXyzAqPQSmxyByi

```

#### Masternodes (and ZSMR)

Masternodes will be supported with a collateral requirement of **15,000 WAE**.  

The collateral requirement is a dynamic target value and will be updated for future
releases based on the market price of WEYCOIN and return on investment relative to
its peer group.

Masternode payments do not start until after approximately 5 weeks post launch. More
specifically, after **block height 50400**.  This is an active promotion of Masternode
decentralization via the Zero Start Masternode Reward policy.  This delayed reward
mechanism seeks to provide sufficient time for swap holders and investors alike to set
up nodes.

Once the exact collateral requirement is accumulated inside an applicable wallet, the
associated configured Masternode can be activated.  Note that the node will only start
receiving payments after the aforementioned ZSMR block height.


#### Masternode Payment Rebalancing: **NEW** Reactive Equilibria (REV1)

Unique to WEYCOIN is the use of a new continous activation function based algorithm, 
labelled Reactive Equilibria (REV1), that seeks to rebalance the payments made 
to miners versus Masternodes.  There is a hard limit of 60% of the block reward that 
can be appropriated for Masternode payments; this limit defines the boundary at which 
total supply locked by Masternodes versus total circulation remains below ~13%. 
As the Masternode count increases, the payment to Masternode holders will 
decline in favour of miners in order to support a decentralised ideology.  The
new algorithm is simple in design but highly effective and lays the foundation for
future advancements.  More information abut this feature will be posted on the
[main site](http://weycoinproject.org). 

##### Reactive Equilibria Masternode Payment Rebalancing Profile 
![Alt text](reactive_equilibria.png)


#### **NEW** Segregated Witness 2x/4x

![Alt text](segwit.png)

SegWit2x is a combination of both SegWit and a 2MB hardfork. WEYCOIN has further 
increased the non-SegWit block size to **4MB** from the outset to allow for greater
scalability and utility.  The maximum serialised block size is **16MB** for WEYCOIN. 

WEYCOIN is both lightning network and atomic swap compatible. And unlike 
many other "compatible" altcoins, SegWit, SegWit2x and the larger blocksize are enabled from the outset.

For further information about Segregated Witness please visit [bitcoincore.org](https://bitcoincore.org/en/2016/01/26/SegWit-benefits/)

##### Segregated Witness Transaction on WEYCOIN Testnet, [block:6635, txid:3fc630ac1a4b91714d7c7150275b8be019152329e70d1f7a37240a7331b9fab6]
![Alt text](testnet_segwit.png)


#### InstantTX and DarkSend Removal 
*(Reproduced here for information purposes only, not release related)*

Dropped support for both InstantTX and DarkSend. With the SegWit upgrade these features are going to be superseeded by far superior technology. SegWit will enable the WEYCOIN to adopt the [Lightning Network](https://lightning.network/lightning-network-paper.pdf), cross-chain atomic swaps, advanced versions of [TumbleBit](https://eprint.iacr.org/2016/575.pdf) and more.


#### Hierarchical Deterministic Key Generation 
*(Reproduced here for information purposes only, not release related)*

Newly created wallets will use hierarchical deterministic key generation
according to BIP32 (keypath m/0'/0'/k').
Existing wallets will still use traditional key generation.

Backups of HD wallets, regardless of when they have been created, can
therefore be used to re-generate all possible private keys, even the
ones which haven't already been generated during the time of the backup.
**Attention:** Encrypting the wallet will create a new seed which requires
a new backup!

Wallet dumps (created using the `dumpwallet` RPC) will contain the deterministic
seed. This is expected to allow future versions to import the seed and all
associated funds, but this is not yet implemented.

HD key generation for new wallets can be disabled by `-usehd=0`. Keep in
mind that this flag only has affect on newly created wallets.
You can't disable HD key generation once you have created a HD wallet.

There is no distinction between internal (change) and external keys.

HD wallets are incompatible with older versions of Bitcoin Core.

[Pull request](https://github.com/bitcoin/bitcoin/pull/8035/files), [BIP 32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)


#### Signature validation using libsecp256k1
*(Reproduced here for information purposes only, not release related)*

ECDSA signatures inside Bitcoin transactions now use validation using
[libsecp256k1](https://github.com/bitcoin-core/secp256k1) instead of OpenSSL.

Depending on the platform, this means a significant speedup for raw signature
validation speed. The advantage is largest on x86_64, where validation is over
five times faster. In practice, this translates to a raw reindexing and new
block validation times that are less than half of what it was before.

Libsecp256k1 has undergone very extensive testing and validation.

A side effect of this change is that libconsensus no longer depends on OpenSSL.


#### Direct headers announcement (BIP 130)
*(Reproduced here for information purposes only, not release related)*

Between compatible peers, [BIP 130](https://github.com/bitcoin/bips/blob/master/bip-0130.mediawiki)
direct headers announcement is used. This means that blocks are advertised by
announcing their headers directly, instead of just announcing the hash. In a
reorganization, all new headers are sent, instead of just the new tip. This
can often prevent an extra roundtrip before the actual block is downloaded.


__________________________________________________________________________


### Signatum Swap and Developers Premine Information

In the spirit of full transparency please read the following information carefully and ask questions on the WEYCOIN Discord server if you are unsure of anything.

#### No Technical Association with Signatum

This is a new digital currency and it shares no technical association to Signatum other than its superficial placeholder name and proposed “proof-of-burn” style swap mechanics.  This is simply a free coin-swap to a new and much better currency, where you are invited to swap your Signatum coins towards.  Under no circumstance are you forced to do so.  It is simply a gesture we have decided to extend to the Signatum community in the light of the recent scam by the old Signatum developers and emotional turbulence that Signatum investors have experienced.  The whole team was in agreement that this was a better alternative in order to preserve value for Signatum investors and help promote a clean, trustworthy and community orientated cryptocurrency sector.


#### The Coin Swap Community Poll

The coin swap poll was initiated on October the 30th and concluded on Saturday the 4th November.  From the poll-data it is evident that the community is in great favour of the 4:1 swap, which includes burning the Signatum coins that will be received during the swap process.  Across Bitcointalk and Discord 319 community members passed their vote.  An overwhelming 85.27% of voters were in favour of the 4:1 swap and burning the coins in the process, while just 14.73% preferred the 20:1 option that would have allowed them to keep their Signatum coins after the swap.  As the community has spoken and decided on the matter, we will initiate a 4:1 coin swap and burn all Signatum coins that we receive in the process.  We personally also believe this to be the best option, as it ensures that fewer people may be affected by the Signatum situation going forward.  Nobody should profit at the expense of others, simply because they may not have the full overview of the situation when purchasing.


#### The Swap and Developers Funds

Instead of premine, primarily due to the new REV1 payment rebalancing algorithm requiring tracking of supply information, an instamine was added to Block 1 for the total of **41,215,000 WAE**.  

The calculation of the swap and developer funds buffer is as follows:

```
Swap Ratio: 4 SIGT : 1 WAE 
Signatum Circulation (approx): 137,000,000 SIGT 
Assumed Circulation for Swap (0.36% buffer): 137,500,000 SIGT
*(Buffer covers 30 days swap period POS generation)*

WEYCOIN Swap Allocation: 34,375,000 WAE
WEYCOIN Swap Allocation (% of Max Supply): 22.9%

WEYCOIN Developers Allocation: 6,875,000 WAE
WEYCOIN Developers Allocation (% of Max Supply): 4.6%
```

Coins that remain unswapped of the initial dedicated swap supply: 60% will be dedicated towards the treasury fund and 40% will be used for air-drops (with minor requirements to increase exposure and awareness).  Full transparency will be provided and users are encouraged to track primary swap funds address.


```
Swap and Developer Funds Address(es):

[0] SUUTsZhb7cpXNgZbieKFrE8gocAtL7EK1C


Block Hash:

[1] 00000b6321951f2ed170bbc9b7a360995176f2df418b0e275149bfce2fde3d6c

{
  "hash": "00000b6321951f2ed170bbc9b7a360995176f2df418b0e275149bfce2fde3d6c",
  "confirmations": 82,
  "strippedsize": 248,
  "size": 248,
  "weight": 992,
  "height": 1,
  "version": 805306387,
  "versionHex": "30000013",
  "merkleroot": "4f70027abe261ca60e37ede92a988594be405dca13bdcbab915872e79ee5ff46",
  "tx": [
    "4f70027abe261ca60e37ede92a988594be405dca13bdcbab915872e79ee5ff46"
  ],
  "time": 1510792676,
  "mediantime": 1510792676,
  "nonce": 3848,
  "bits": "1e0fffff",
  "difficulty": 0.0002441371325370145,
  "chainwork": "0000000000000000000000000000000000000000000000000000000000200011",
  "previousblockhash": "00000df14d859c4b3219d93978bcf02afc123d2344a2ed39033e1208948aa7c0",
  "nextblockhash": "000001c4bb98a9d3863d26325d95d3ed774309a605c9b0b18746f14e50253a4c"
}

Coinbase Transaction:

{
  "txid": "4f70027abe261ca60e37ede92a988594be405dca13bdcbab915872e79ee5ff46",
  "hash": "4f70027abe261ca60e37ede92a988594be405dca13bdcbab915872e79ee5ff46",
  "size": 167,
  "vsize": 167,
  "version": 2,
  "locktime": 0,
  "vin": [
    {
      "coinbase": "510101",
      "sequence": 4294967295
    }
  ],
  "vout": [
    {
      "value": 41250000.00000000,
      "n": 0,
      "scriptPubKey": {
        "asm": "OP_DUP OP_HASH160 4ec371eeab928ff421d09f9ed54ec1c98098ab50 OP_EQUALVERIFY OP_CHECKSIG",
        "hex": "76a9144ec371eeab928ff421d09f9ed54ec1c98098ab5088ac",
        "reqSigs": 1,
        "type": "pubkeyhash",
        "addresses": [
          "SUUTsZhb7cpXNgZbieKFrE8gocAtL7EK1C"
        ]
      }
    }, 
    {
      "value": 0.00000000,
      "n": 1,
      "scriptPubKey": {
        "asm": "OP_HASH160 1343c8390c5f73d608f4b47e6959d8f3ae863605 OP_EQUAL",
        "hex": "a9141343c8390c5f73d608f4b47e6959d8f3ae86360587",
        "reqSigs": 1,
        "type": "scripthash",
        "addresses": [
          "33Ssxmn3ehVMgyxgegXhpLGSBpubPjLZQ6"
        ]
      }
    }, 
    {
      "value": 0.00000000,
      "n": 2,
      "scriptPubKey": {
        "asm": "OP_RETURN aa21a9ede2f61c3f71d1defd3fa999dfa36953755c690689799962b48bebd836974e8cf9",
        "hex": "6a24aa21a9ede2f61c3f71d1defd3fa999dfa36953755c690689799962b48bebd836974e8cf9",
        "type": "nulldata"
      }
    }
  ]
}
```


#### The Swap Mechanics

Development of a Discord sever bot that will be used for the coin swap process in December is in full flow.

Users will use the bot on Discord, to initiate and conclude their coin-swap.  The specifics of how to perform the coin-swap will be communicated on November 29th.  We will make sure that everyone are notified across all channels, so that nobody may miss out on the coin-swap opportunity.

Once the swap-process is initiated, Signatum coin-holders will have a 30 day window, whereby they can swap their coins from Signatum to WEYCOIN at the 4:1 ratio.

__________________________________________________________________________


### Acknowledgements 

Credit goes to Bitcoin Core, Dash and Bitsend for providing a basic platform for 
WEYCOIN to enhance and develop, in concert with a shared desire to support the
adoption of a decentralised digital currency future for the masses.


__________________________________________________________________________


### License

WEYCOIN Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.


__________________________________________________________________________


### Development Process

The `master` branch is meant to be stable. Development is normally done in separate branches.
[Tags](https://github.com/weycoin/weycoin/tags) are created to indicate new official,
stable release versions of WEYCOIN' Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).


__________________________________________________________________________


### Building process

**compiling WEYCOIN from git**

Use the autogen script to prepare the build environment.

    ./autogen.sh
    ./configure
    make

**precompiled binaries**

Precompiled binaries are available at GitHub, see
https://github.com/weycoin/weycoin/releases

Always verify the signatures and checksums.


__________________________________________________________________________
