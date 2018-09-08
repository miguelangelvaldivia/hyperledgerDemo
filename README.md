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
# clone this repo into your AWS AMI
https://github.com/miguelangelvaldivia/hyperledgerDemo.git
# set appropriate permissions on scripts folder 
chmod 600 scripts
# and the bash files that contains
cd scripts
chmod 400 buildF1.sh
chmod 400 buildF2.sh
chmod 400 startFabric.sh
chmod 400 stopFabric.sh
```
You could add `scripts` to your `PATH` or
```sh
# invoke the bash from scripts folder
# use source for buildF1.sh
source scripts/buildF1.sh
# reboot the EC2
# log back in and make sure that ubuntu is part of group docker
groups
# continue with buildF2.sh
./scripts/buildF2.sh
```
After `buildF2.sh` a network will have been started.  Log in into a separate terminal with a CLI session.
