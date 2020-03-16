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

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
