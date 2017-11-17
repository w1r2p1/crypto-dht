# crypto-dht
Experimental Blockchain over DHT

## Info

Based on my own DHT implementation in GO

![Screenshot](https://github.com/champii/crypto-dht/raw/master/screenshot.png "Screenshot")

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
  -f value, --folder value   Base Folder (default: "/home/champii/.crypto-dht")
  -i                         Interactif
  -s                         Stat mode
  -S value, --send value     Send coins from main.key. Must be of the form 'amount:destAddress'
  -m                         Mine
  -w                         Show wallets and amount
  -g                         Deactivate GUI
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

- Deactivate GUI for some commands (-n, -s, -S, -i)
- Store unspentTxOut and blockHeigh on disk to avoid resync all the chain each time
- DHT's OnStore to avoid saving bad blocks
- Merkel tree
- Better GUI
- Fix that "bad block" error that pop's sometimes
- Transactions history for a wallet
- Manage wallets
- Recheck blockchain
- Config file
- Daemon ?
