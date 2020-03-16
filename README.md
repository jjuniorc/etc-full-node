# etc-full-node
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

### Installing

A step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
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
