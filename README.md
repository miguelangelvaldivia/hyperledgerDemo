# HyperledgerDemo
Sets up prerequisites and does a fresh installation of Hyperledger Fabric. The scripts are tailor made for an AWS AMI over an ubuntu user.

## Scripts
There are four scripts in the scripts folder:
- buildF1.sh
- buildF2.sh
- startFabric.sh
- stopFabric.sh

### buildF1.sh
Installs the prerequisites go, docker, python and docker-compose
### buildF2.sh
Downloads Fabric and starts the network for exercise <i>e2e_cli</i>.
### startFabric.sh
Starts the network for exercise sample <i>e2e_cli</i>.
### stopFabric.sh
Stops the network for exercise sample <i>e2e_cli</i>.  This script is called from the cron service daily.

## Install
Prepare the environment.  Log into your EC2 instance (I chose Ubuntu 16.04). Create new directory <i>scripts</i> under your HOME directory.

```sh
cd ~
git clone https://github.com/hyperledger/fabric.git
# copy contents of buildF into the shell
```

Clone the repo and find a a script to install the prerequisites for Fabric as well as build latest version of Fabric:
'source scripts/buidF1.sh'
Use source to invoke this bash. Installs go, python, docker and docker-compose
reboot the EC2.
Verify that user "ubuntu" is in the "docker" group
Run the second script:
'./scripts/buildF2.sh'
