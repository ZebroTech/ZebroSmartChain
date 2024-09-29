## Zebro Smart Chain (ZSC)

![zsc](https://user-images.githubusercontent.com/32578764/227735463-774604d0-d53f-4cd1-b01d-1755146f693c.png)

#### ZSC is ethereum based layer2 blockchain with Ethash fixed supply Proof of Work [PoW] consesus

#### Go-Zebro is go client to run Zebro Smart Chain 

The goal of Zebro Smart Chain (ZSC) is to bring programmability and interoperability to Project Zebrocoin. In order to embrace the existing popular community and advanced technology, it will bring huge benefits by staying compatible with all the existing smart contracts on Ethereum and Ethereum tooling. And to achieve that, the easiest solution is to develop based on go-ethereum fork, as we respect the great work of Ethereum very much.

Zebro Smart Chain (ZSC) starts its development based on go-ethereum fork. So you may see many toolings, binaries and also docs are based on Ethereum ones, such as ethereum remix IDK for compiling and deploying of token/dApp contracts.

[![API Reference](
https://camo.githubusercontent.com/915b7be44ada53c290eb157634330494ebe3e30a/68747470733a2f2f676f646f632e6f72672f6769746875622e636f6d2f676f6c616e672f6764646f3f7374617475732e737667
)](https://pkg.go.dev/github.com/ethereum/go-ethereum?tab=doc)
[![Discord](https://img.shields.io/badge/discord-join%20chat-blue.svg)](https://discord.gg/z2VpC455eU)

From that baseline of EVM compatible, Zebro Smart Chain introduces PoW consensus that can support short block time and lower fees. The all bonded nodes will become validators and produce blocks. The double-sign detection and other slashing logic guarantee security, stability, and chain finality.

Cross-chain transfer and other communication are possible due to native support of interoperability. Relayers and on-chain contracts are developed to support that. ZEBRO-SWAP ZEBRO-STAKE ZEBRO-BRIDGE remain liquid venue of the exchange. This chain architecture will be ideal for users to take advantage of the fast trading on one side and build their decentralized apps on the other side. **The Zebro Smart Chain** will be:

- **A self-sovereign blockchain**: Provides security and safety with all nodes.
- **EVM-compatible**: Supports all the existing Ethereum tooling along with faster finality and cheaper transaction fees.
- **Interoperable**: Comes with efficient native chain communication; Optimized for scaling high-performance dApps that require fast and smooth user experience.
- **Distributed with on-chain governance**: Proof of Work brings in decentralization and community participants. As the native token, ZEBRO will serve as both the gas of smart contract execution and tokens for staking.

More details in [White Paper](https://zebrocoin.app/download/).



## Key features

### Supported Wallets
Zebro Smart Chain (ZSC) is an Ethereum Virtual Machine (EVM) compatible chain which could be added to any of EVM compatible hardware, software or browser extension wallets such as Metamask, Trust Wallet, Binance Chain Wallet, Trexor etc. 

### Proof of Work 
Although Proof-of-Work (PoW) has been approved as a practical mechanism to implement a decentralized network, it is a friendly to the environment and also any node can participate in network. 

Proof-of-Work(PoW) provides some defense to 95% attack, with improved efficiency, stability and security.

Proof-of-Work(PoW) increases the decentralization and favors community governance. 

Zebrocoin ZEBRO total/maximum supply is capped by 10 Billion ZEBRO, 5 Billion out of 10 Billion ZEBROs will be locked forever to bridge-contracts to bridging ZEBRO to wZEBRO on BSC, Polygon, Fantom and Phoenix blockchain. Maximum gas limit of block is set to 5 ZEBRO per block in favor of mining nodes.

All 10 Billion ZEBROs are allocated to Zebrocoin owner in genesis block to prevent inflation in maximum/circulation supply, miners can join network and mine for transaction fee.

Zebro Smart Chain PoW consesus benefits:

1. Blocks are produced by any miner node to mine for transaction fee upto 5ZEBRO per block.
2. Regular Miner receives transaction fee from spender for mining of a block while Super Miner receives transaction fee from spender plus 100 ZEBRO from super_miner contract for mining of a block.
3. Miner nodes can use Ethereum's Ethhash consensus engine to mine blocks.
4. All miner nodes are validators which gives Zebro Smart Chain 100% decentralized concept.
5. Transaction fee will be changed according to market price to encourage ZEBRO miners and give ease to users in txn fee.
6. Ethash Proof-of-Work(PoW) consensus engine will interact as an Etherem PoW concept.

 
### Light Client of Zebro Smart Chain  

To achieve the communication to Zebro Smart Chain, need introduce a on-chain light client verification algorithm.
It contains two parts:

1. [Stateless Precompiled contracts](https://github.com/ZebroTech/ZSC/blob/master/core/vm/contracts_lightclient.go) to do tendermint header verification and Merkle Proof verification.
2. [Stateful solidity contracts](https://github.com/ZebroTech/zsc-genesis-contract/blob/master/contracts/TendermintLightClient.sol) to trusted appHash.  



## Native Token

Zebrocoin ZEBRO will run on Zebro Smart Chain in the same way as ETH runs on Ethereum so that it remains as `native token` for ZSC. This means, 
ZEBRO will be used to:

1. pay `gas` to deploy or invoke Smart Contract on ZSC
2. perform cross-chain operations, such as transfer token assets across Zebro Smart Chain.



## Building the source

GoZebro is Go client to run ZSC node.

Many of the below are the same as or similar to go-ethereum.

For prerequisites and detailed build instructions please read the [Installation Instructions](https://zebrocoin.app/docs/).

Building `gozebro` requires both a Go (version 1.20 or later) and a C compiler. You can install
them using your favourite package manager. Once the dependencies are installed, run

```shell
make gozebro
```

or, to build the full suite of utilities:

```shell
make all
```


## Executables

The zsc project comes with several wrappers/executables found in the `cmd`
directory.

|    Command    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| :-----------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  **`gozebro`**   | Main Zebro Smart Chain client binary. It is the entry point into the ZSC network (main-, test- or private net), capable of running as a full node (default), archive node (retaining all historical state) or a light node (retrieving data live). It has the same and more RPC and other interface as go-ethereum and can be used by other processes as a gateway into the ZSC network via JSON RPC endpoints exposed on top of HTTP, WebSocket and/or IPC transports. `gozebro --help` and the [CLI page](https://zebrocoin.app/docs/) for command line options.          |
|   `clef`      | Stand-alone signing tool, which can be used as a backend signer for `gozebro`.  |
|   `devp2p`    | Utilities to interact with nodes on the networking layer, without running a full blockchain. |
|   `abigen`    | Source code generator to convert Ethereum contract definitions into easy to use, compile-time type-safe Go packages. It operates on plain [Ethereum contract ABIs](https://docs.soliditylang.org/en/develop/abi-spec.html) with expanded functionality if the contract bytecode is also available. However, it also accepts Solidity source files, making development much more streamlined. Please see our [Native DApps](https://zebrocoin.app/docs/) page for details. |
|  `bootnode`   | Stripped down version of our Ethereum client implementation that only takes part in the network node discovery protocol, but does not run any of the higher level application protocols. It can be used as a lightweight bootstrap node to aid in finding peers in private networks.                                                                                                                                                                                                                                                                 |
|     `evm`     | Developer utility version of the EVM (Ethereum Virtual Machine) that is capable of running bytecode snippets within a configurable environment and execution mode. Its purpose is to allow isolated, fine-grained debugging of EVM opcodes (e.g. `evm --code 60ff60ff --debug run`).                                                                                                                                                                                                                                                                     |
|   `rlpdump`   | Developer utility tool to convert binary RLP ([Recursive Length Prefix](https://eth.wiki/en/fundamentals/rlp)) dumps (data encoding used by the Ethereum protocol both network as well as consensus wise) to user-friendlier hierarchical representation (e.g. `rlpdump --hex CE0183FFFFFFC4C304050583616263`).                                                                                                                                                                                                                                 |



## Running `gozebro`

Going through all the possible command line flags is out of scope here (please consult our
[CLI Wiki page](https://zebrocoin.app/docs/)),
but we've enumerated a few common parameter combos to get you up to speed quickly
on how you can run your own `gozebro` instance.

### Hardware Requirements

The hardware must meet certain requirements to run a full node.
- VPS running recent versions of Mac OS X or Linux.
- 100GB of SSD storage for mainnet, 5G of SSD storage for testnet.
- 8 cores of CPU and 32 gigabytes of memory (RAM) for mainnet.
- 1 or more static IP assigned to VPS.
- A broadband Internet connection with upload/download speeds of at least 10 megabyte per second

```shell
$ gozebro console
```

This command will:
 * Start `gozebro` in fast sync mode (default, can be changed with the `--syncmode` flag),
   causing it to download more data in exchange for avoiding processing the entire history
   of the Zebro Smart Chain network, which is very CPU intensive.
 * Start up `gozebro`'s built-in interactive [JavaScript console](https://geth.ethereum.org/docs/interface/javascript-console),
   (via the trailing `console` subcommand) through which you can interact using [`web3` methods](https://web3js.readthedocs.io/) 
   (note: the `web3` version bundled within `gozebro` is very old, and not up to date with official docs),
   as well as `gozebro`'s own [management APIs](https://zebrocoin.info/docs/).
   This tool is optional and if you leave it out you can always attach to an already running
   `gozebro` instance with `gozebro attach`.

### Running a Full node

Steps:

1. Download the binary, config and genesis files from [release](https://github.com/ZebroTech/ZSC/releases/tag/v1.1.11), or compile the binary by `make gozebro`. 
2. Init genesis state: `./gozebro --datadir node init gozebroGenesis.json`.
3. Start your fullnode: `./gozebro --config ./config.toml --datadir ./node`.
4. Or start a validator node: `./gozebro --config ./config.toml --datadir ./node -unlock --mine --allow-insecure-unlock`. 

*Note: The default p2p port is 30311 and the RPC port is 8575 which is different from Ethereum.*

More details about [running a node](https://zebrocoin.app/gozebro/) and [becoming a miner](https://zebrocoin.app/mining/)

<!--https://zebrocoin.info/zsc/docs NO SUCH FILE-->

*Note: Although there are some internal protective measures to prevent transactions from
crossing over between the main network and test network, you should make sure to always
use separate accounts for play-money and real-money. Unless you manually move
accounts, `gozebro` will by default correctly separate the two networks and will not make any
accounts available between them.*


### Gozebro genesis file
gozebroGenesis.json

```shell
{
  "config": {
    "chainId": 786786,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "istanbulBlock": 0,
    "berlinBlock": 0,
    "ethash": {}
  },
  "difficulty": "1",
  "gasLimit": "5000000000000000000",
  "alloc": {
    "45Cf35822345779b1b799795Ee4B32020a3cF0Bb": { "balance": "10000000000000000000000000000" }
  }
}
```
### Zebro Smart Chain (ZSC) enodes
enode1 
```shell
"enode://e291b01ac57d9199b69405baff1a730d8c9bff7a8085b400b5353c165a0ac45b2e318063baf6c9c043033a5282649003e785c4abc83f6eb3cac3370c127ca455@167.86.104.54:30397?discport=0"
```
enode2
```shell
"enode://29f2640f50cca2952deb5869ebcec011f52495c88130791144985bb8aa233bf15695c564b1d9a7f45bfd71b7d03ce1c662b2673d0086e60fc2de605dbbb873ac@144.91.88.149:57640?discport=0"
```

### Configuration

As an alternative to passing the numerous flags to the `gozebro` binary, you can also pass a
configuration file via:

```shell
$ gozebro --config /path/to/your_config.toml
```

To gozebro an idea how the file should look like you can use the `dumpconfig` subcommand to
export your existing configuration:

```shell
$ gozebro --your-favourite-flags dumpconfig
```

### Programmatically interfacing `gozebro` nodes

As a developer, sooner rather than later you'll want to start interacting with `gozebro` and the
Zebro Smart Chain network via your own programs and not manually through the console. To aid
this, `gozebro` has built-in support for a JSON-RPC based APIs ([standard APIs](https://eth.wiki/json-rpc/API)
and [`gozebro` specific APIs](https://zebrocoin.app/docs/r)).
These can be exposed via HTTP, WebSockets and IPC (UNIX sockets on UNIX based
platforms, and named pipes on Windows).

The IPC interface is enabled by default and exposes all the APIs supported by `gozebro`,
whereas the HTTP and WS interfaces need to manually be enabled and only expose a
subset of APIs due to security reasons. These can be turned on/off and configured as
you'd expect.

HTTP based JSON-RPC API options:

  * `--http` Enable the HTTP-RPC server
  * `--http.addr` HTTP-RPC server listening interface (default: `localhost`)
  * `--http.port` HTTP-RPC server listening port (default: `8545`)
  * `--http.api` API's offered over the HTTP-RPC interface (default: `eth,net,web3`)
  * `--http.corsdomain` Comma separated list of domains from which to accept cross origin requests (browser enforced)
  * `--ws` Enable the WS-RPC server
  * `--ws.addr` WS-RPC server listening interface (default: `localhost`)
  * `--ws.port` WS-RPC server listening port (default: `8546`)
  * `--ws.api` API's offered over the WS-RPC interface (default: `eth,net,web3`)
  * `--ws.origins` Origins from which to accept websockets requests
  * `--ipcdisable` Disable the IPC-RPC server
  * `--ipcapi` API's offered over the IPC-RPC interface (default: `admin,debug,eth,miner,net,personal,txpool,web3`)
  * `--ipcpath` Filename for IPC socket/pipe within the datadir (explicit paths escape it)

You'll need to use your own programming environments' capabilities (libraries, tools, etc) to
connect via HTTP, WS or IPC to a `gozebro` node configured with the above flags and you'll
need to speak [JSON-RPC](https://www.jsonrpc.org/specification) on all transports. You
can reuse the same connection for multiple requests!

**Note: Please understand the security implications of opening up an HTTP/WS based
transport before doing so! Hackers on the internet are actively trying to subvert
ZSC nodes with exposed APIs! Further, all browser tabs can access locally
running web servers, so malicious web pages could try to subvert locally available
APIs!**



## Mining ZEBRO
Zebro Smart Chain (ZSC) is PoW Ethereum charecteristic blockchain with supply limit capped by 10 billion coins, all 10 billion coins were generated in block '0". Miners have 2 mining options 1 Regular Miner (mine for txn fee), 2 Super Miner (mine for block rewards).

### Regular Miner (Mining for txn fee)
To mine for txn fee miner must run a full node on server and set_miner. Regular miners get txn fee for mining of a block with txn(s) in it. Currently txn fee is 0.00005 ZEBRO to 0.00021 ZEBRO per txn. Txn fees are paid by ZEBRO users for txns they made on ZSC.

### Super Miner (Mining for block reward)
To mine for block reward miner must run full node on server set_miner and send colletoral 2 million ZEBRO from miner address to a contract on ZSC. Super miners get reward 100 ZEBRO per each block mined. This reward is not newly generated token but reward sent from contract to Super Miner for mining each block successfully. ZSC Block Timespan is 15 seconds, new block generated every 15 seconds.



## Contribution

Thank you for considering to help out with the source code! We welcome contributions
from anyone on the internet, and are grateful for even the smallest of fixes!

If you'd like to contribute to zsc, please fork, fix, commit and send a pull request
for the maintainers to review and merge into the main code base. If you wish to submit
more complex changes though, please check up with the core devs first on [our discord channel](https://discord.gg/d6hAEbU8CG)
to ensure those changes are in line with the general philosophy of the project and/or get
some early feedback which can make both your efforts much lighter as well as our review
and merge procedures quick and simple.

Please make sure your contributions adhere to our coding guidelines:

 * Code must adhere to the official Go [formatting](https://golang.org/doc/effective_go.html#formatting)
   guidelines (i.e. uses [gofmt](https://golang.org/cmd/gofmt/)).
 * Code must be documented adhering to the official Go [commentary](https://golang.org/doc/effective_go.html#commentary)
   guidelines.
 * Pull requests need to be based on and opened against the `master` branch.
 * Commit messages should be prefixed with the package(s) they modify.
   * E.g. "eth, rpc: make trace configs optional"

Please see the [Developers' Guide](https://zebrocoin.app/docs/)
for more details on configuring your environment, managing project dependencies, and
testing procedures.



## License

The zsc library (i.e. all code outside of the `cmd` directory) is licensed under the
[MIT General Public License](https://zebrotech.mit-license.org/).

The zsc binaries (i.e. all code inside of the `cmd` directory) is licensed under the
[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html), also
included in our repository in the `COPYING` file.
