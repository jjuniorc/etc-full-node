# Ethereum Classic Full Node
Create a Ethereum Classic Full Node Mainnet (Livenet) and Mordor Testnet, both tested running at the same server.

## Getting Started

Create a cloud or local machine (VM should be great). All scripts and instructions was tested on Ubuntu 18.04 LTS.

### Prerequisites

Disk Storage: Minimum 500 GB, ideal 1.5 TB.

For each network create a separated sudo user:
```
sudo adduser etcmainnet
<Type a password and name>
sudo usermod -aG sudo etcmainnet
su - etcmainnet
```

```
sudo adduser etctestnet
<Type a password and name>
sudo usermod -aG sudo etctestnet
su - etctestnet
```
Download the Parity executable at /usr/local/bin directory. In this example was used version 2.7.2: https://releases.parity.io/ethereum/v2.7.2/x86_64-unknown-linux-gnu/parity
After download parity executable, give owner permissions for current user and execute permissions for file and put it in /usr/local/bin:

```
sudo chown etcmainnet parity
sudo chmod +x parity
sudo cp parity /usr/local/bin
source ~/.bashrc
parity --version
```
Obs.: Geth executable can be used instead, but parity seems fastest to integrate external apps to full node.

### Installing

Create the blockchain directory at user directory
```
cd ~
mkdir blockchain
mkdir blockchain/db
```

Test Parity running using blockchain directory as base path. The command below specify to open all communication ports and block download with pruning fast (1 GB of cache size) for a non ssd disk. Check the Parity documentation for your server configuration at https://wiki.parity.io/Configuring-Parity-Ethereum.

```
parity --chain classic --base-path /home/etcmainnet/blockchain --identity "LivenetETCNode" --db-path /home/etcmainnet/blockchain/db --cache-size 1024 --unsafe-expose --port 30303 --jsonrpc-port 8545 --jsonrpc-interface all --jsonrpc-apis all --jsonrpc-hosts all --jsonrpc-cors all --ws-port 8546 --ws-interface all --ws-apis all --ws-origins all --ws-hosts all --no-ancient-blocks --warp --geth --mode active --pruning fast --db-compaction hdd
```

After start you'll be able to test api access using your browser by the address:

```
http://<YOUR SERVER IP OR NAME>:8545/api/health
```

Stop the Parity using CTRL+C command.

## Daemon execution

You can install Screen to easily run background process.
```
sudo apt install screen
```

Now you'll be able to attach full node process to another background screen.
```
cd /home/etcmainnet

screen -dmSL scretcmainnet parity --chain classic --base-path /home/etcmainnet/blockchain --identity "LivenetETCNode" --db-path /home/etcmainnet/blockchain/db --cache-size 4096 --unsafe-expose --port 30303 --jsonrpc-port 8545 --jsonrpc-interface all --jsonrpc-apis all --jsonrpc-hosts all --jsonrpc-cors all --ws-port 8546 --ws-interface all --ws-apis all --ws-origins all --ws-hosts all --warp --geth --mode active --pruning fast --db-compaction hdd
```

Every time you need to see background or stop with CTRL+C the process, you can attach the screen by command:
```
screen -x scretcmainnet
```

To deattach use the key CTRL+A and press D.

### Server consumption

Using Node.JS and Web3.js as example of Full node server consumption.

View Node Sync Status (The 8545 port is the RPC port passed in Parity start):
```
var networkAddress = 'http://<YOUR SERVER IP OR NAME>:8545';
var Web3 = require("web3");
var web3 = new Web3();
web3.setProvider(new web3.providers.HttpProvider(networkAddress));

web3.eth.isSyncing().then(function (r)
{
    console.log(r); //Eg. currentBlock and highestBlock
}).catch((error)=>{
    console.log(error);
});
```

Check Wallet Address Ether Balance:
```
var networkAddress = 'http://<YOUR SERVER IP OR NAME>:8545';
const Web3 = require('web3');
const web3 = new Web3( new Web3.providers.HttpProvider(networkAddress) );

web3.eth.getBalance(address, function (error, result) {
    if (!error)
    {
        var EtherBalance = web3.utils.fromWei(result,'ether');
        console.log(EtherBalance);
    }
    else
    {
        //any other error
        console.log(error);
    }
});
```

## Deployment

A Full Node complete integration could be done buy creating routines like Transaction Info, Transfer, Create Contract, etc. Web3.js is a good tool able to deal with those functionalities.

## Built With

* [Parity](https://www.parity.io/) - Ethereum Network Client Application
* [Node.js](https://nodejs.org/) - Javascript C++ Backend Runtime
* [Web3.js](https://github.com/ethereum/web3.js) - Ethereum Javascript API

## Authors

* **João Costa** (https://github.com/jjuniorc)
