# crypto-dht
Experimental Blockchain over DHT

## Background

A Decentralized Hash Table (DHT) is a form of network used to store some content
in the form of key/value pairs. It differs from classical hash tables from its 
decentralized nature. In fact, each node participating in a DHT can fetch and store
addressable content by key, as well as storing and serving a fraction of that hash table.

Bitcoin based blockchains all share the same characteristic: In order to reach 
a consensus, each and every nodes participating in the network have to keep a 
full copy of the blockchain. Even if this issue has been solved with light wallets
and other trust-based protocol, a majority of the nodes need to keep a full copy
of the blockchain in order for the network to keep working well.

This experimental project is a try to avoid to keep all the blockchain, but instead
store it in a DHT. This way every node has to keep a small
portion of the blocks, depending on its own address in the DHT, the number of keys stored
and the number of nodes participating in the network.

Even if the blocks are stored in a decentralized way, every node still have to keep
some records when mining time has come:
- Every block's header, to validate a block when it comes for storage
- Every UTXOs (Unspent Transaction Output, basicaly forming the balances of
every wallet) in order to validate incoming transactions
- By extension every known address (wallet) that hold or have held some coins

This client is implemented following the list above.

## Info

Based on my own DHT implementation in GO: [go-dht](https://github.com/champii/go-dht)

- One block every minute
- Base block revenue is 1.00 coin (100 cents)
- DHT for block storage.

![Screenshot](https://github.com/champii/crypto-dht/raw/master/screenshot.png "Screenshot")
![Screenshot2](https://github.com/champii/crypto-dht/raw/master/screenshot2.png "Screenshot2")
![Screenshot3](https://github.com/champii/crypto-dht/raw/master/screenshot3.png "Screenshot3")


## Usage

```
NAME:
  Crypto-Dht - Experimental Blockchain over DHT

USAGE:
  crypto-dht [options]

VERSION:
  0.1.0

OPTIONS:
  -c value, --connect value  Connect to node ip:port. If not set, startup a bootstrap node.
  -l value, --listen value   Listening address and port (default: "0.0.0.0:3000")
  -f value, --folder value   Config Folder (default: "/home/champii/.crypto-dht")
  -s                         Stat mode
  -m                         Mine
  -w                         Show wallets and amount
  -g                         Deactivate GUI
  -S value, --send value     Send coins from main.key. Must be of the form 'amount:destAddress'
  -n nodes, --network nodes  Spawn X new nodes network. If -b is not specified, a new network is created. (default: 0)
  -v level, --verbose level  Verbose level, 0 for CRITICAL and 5 for DEBUG (default: 3)
  -h, --help                 Print help
  -V, --version              Print version
```

## Build

```
$> go get -u github.com/asticode/go-astilectron-bundler/...
$> ./scripts/build.sh
```

The output binary will be in `./build/linux-amd64/crypto-dht`

## Todo

- handle forks
- Dont permanently sync but rather use broadcast to spread and listen to new blocks
- Hash pub key to make addresses shorter
- (Make DHT address the hash of the wallet? anonymity may be compromised, don't allow for multiple connexions with same address)
- Get pending transactions from other nodes
- Fees
- Scrypt
- Better GUI
- Manage wallets
- Recheck blockchain
- Config file
- Daemon ?
