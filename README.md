<div align="center">

# DISCLAIMER AND TERMS

## This is a workaround ONLY for the commit-success-but-reveal-failure transactions executed by the miraland-atomicals-js. The failed transactions coming from atomicalsir are not supported at this time. Please be aware that this product/tool has been built in haste with very limited testing. Use it at your own discretion.

## The product is provided 'AS IS', without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and non-infringement. In no event shall the creators, authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with The Product or the use or other dealings in The Product. The Product does not represent any investment, security, financial instrument, redemption, promise, bearer instrument or commitment of any kind. The Product is intended only for educational and experimentation purposes only and is not backed or supported by any individual or team. There are no future prospects or plans of any kind beyond the educational and experimentation usages of The Product. Any use or interaction with The Product is expressly prohibited unless your jurisdiction and circumstances explicitly permits the use and interaction with The Product. Any interaction with The Product constitutes acceptance of these terms and the user accepts all responsibility and all risks associated with the use and interaction with The Product.

<div>

## Usage
```
Miraland Atomicals-js Tool for Resuming after Commit Succeeded but Reveal Failed (based on miraland-atomicals-js derived from atomicals-js)

Usage: yarn cli [OPTIONS] mint-dft <TICKER> --satesbyte <TRY_SAME_SATSBYTE_AS_COMMIT_FIRST> --committime <COMMIT_TIMESTAMP> --commitnonce <COMMIT_NONCE> --commitspk <COMMIT_SCRIPT_PUBKEY>

Here only list transaction recovery related options.
Options:

      --satsbyte <VALUE>
          First, try using the same satsbyte value as in the previous commit transaction. If it takes a long time waiting utxo, try changing
          it to a value slightly smaller than the one just given.

      --committime <COMMIT_TIMESTAMP>
          Previous commit payload unix timestamp

      --commitnonce <COMMIT_NONCE>
          Previous commit payload nonce

      --commitspk <COMMIT_SCRIPT_PUBKEY>
          Previous commit tx first output script pubkey
```

## Where to find above argument values?

--committime, --commitnonce, looking for the line containing some pattern like ```time: (number)  nonce: (number)``` in console output.

--commitspk, can be found by searching your txid at https://mempool.space, please see screenshots below

For --commit-scriptpk:
![Transaction Overview](/assets/images/tx-overview.png "Transaction Overview")


# Atomicals Javascript Library

> atomicals.xyz
> Documentation: https://docs.atomicals.xyz

![Atomicals](banner.png)


### WARNING: STRONGLY RECOMMENDED TO USE YARN INSTEAD OF NPM

Use `yarn` package manager instead of `npm`. Instructions below (They are: `npm install -g yarn`)

In the latest version of the CLI processing library the option switches (the settings starting with `--`) are not processed correctly and it would lead to
too small of a fee being set and result in your transactions not being mined.

Workaround: Use `yarn` instead of `npm`


### Install, Build and Run Tests

## Install

```
# Download the Github repo:
git clone https://github.com/atomicals/atomicals-js.git

cd atomicals-js

# Build:
# If you don't have yarn & node installed
# npm install -g node
# npm install -g yarn

yarn install
yarn run build

#See all commands at:

yarn run cli --help

```

### Quick Start - Command Line (CLI)

First install packages and build, then follow the steps here to create your first Atomical and query the status. Use `yarn cli`to get a list of all commands available.

#### 0. Environment File (.env)

The environment file comes with defaults (`.env.example`), but it is highly recommend to install and operate your own ElectrumX server. Web browser communication is possible through the `wss` (secure websockets) interface of ElectrumX.

```
ELECTRUMX_WSS=wss://electrumx.atomicals.xyz:50012

// Optional (defaults to wallet.json)
WALLET_PATH=path-to-wallet.json

// The number of concurrent processes to be used. This should not exceed the number of CPU cores available. If not set, the default behavior is to use all available CPU cores minus one.
CONCURRENCY=4
```

_ELECTRUMX_WSS_: URL of the ElectrumX with Atomicals support. Note that only `wss` endpoints are accessible from web browsers.

#### 1. Wallet Setup

The purpose of the wallet is to create p2tr (pay-to-taproot) spend scripts and to receive change from the transactions made for the various operations. _Do not put more funds than you can afford to lose, as this is still beta!_

To initialize a new `wallet.json` file that will store your address for receiving change use the `wallet-init` command. Alternatively, you may populate the `wallet.json` manually, ensuring that the address at `m/44'/0'/0'/0/0` is equal to the address and the derivePath is set correctly.

Configure the path in the environment `.env` file to point to your wallet file. defaults to `./wallet.json`

Default:

```
WALLET_PATH=.
WALLET_FILE=wallet.json
```

Update to `wallets/` directory:

```
WALLET_PATH=./wallets
WALLET_FILE=wallet.json
```

Create the wallet:

```
yarn cli wallet-init

>>>

Wallet created at wallet.json
phrase: maple maple maple maple maple maple maple maple maple maple maple maple
Legacy address (for change): 1FXL2CJ9nAC...u3e9Evdsa2pKrPhkag
Derive Path: m/44'/0'/0'/0/0
WIF: L5Sa65gNR6QsBjqK.....r6o4YzcqNRnJ1p4a6GPxqQQ
------------------------------------------------------
```

#### 2. Explore the CLI

```
yarn cli --help
```

#### 3. Quick Commands

Get all of the commands available:

```
yarn cli --help
```

Read the documentation at https://docs.atomicals.xyz

## ElectrumX Server RPC Interface

See updated ElectrumX (https://github.com/atomicals/atomicals-electrumx)

## Any questions or ideas?

https://atomicals.xyz

https://x.com/atomicalsxyz (X - Formerly Twitter)

## Donate to Atomicals Development

We greatly appreciate any donation to help support Atomicals Protocol development. We worked out of passion and kindness for the world, we believe this technology must exist and be free for all to use. Bitcoin is our one hope for freedom and digital sovereignty and we intend to do our best to make it a reality.

BTC: bc1pa5hvv3w3wjwfktd63zcng6yeccxg9aa90e34n9jrjw3thgc52reqxw6has

![Donate to Atomicals Development](donate.png)
