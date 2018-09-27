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
git clone https://github.com/miguelangelvaldivia/hyperledgerDemo.git
# set appropriate permissions for the bash files
cd scripts
chmod u+x *.sh
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

## Save some money
Once the server is running you may want to turn it down and bring back up at a certain times during the day.  This will avoid charges for running this dev environment overnight.  
Use a combination of services:
- CloudWatch
- a cron service in your EC2

### CloudWatch
Create a Lambda and a schedule service to turn your EC2 up and down.  AWS scheduler is also an option.  Have a look in:
`https://aws.amazon.com/premiumsupport/knowledge-center/start-stop-lambda-cloudwatch/`
### cron service
Add a crontab service to shutdown the Fabric orderly before EC2 schedule shuts it down
```sh
crontab -e
# add this line
45 20 * * * sh /home/ubuntu/scripts/stopFabric.sh 
# this will stop the e2e_cli.sh sample network (if running) ahead of the EC2 scheduled shut down
```
