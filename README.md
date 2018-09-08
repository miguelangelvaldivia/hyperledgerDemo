# hyperledgerDemo
Sets up prerequisites and does a fresh installation of Hyperledger Fabric. The scripts are tailor made for an AWS AMI over an ubuntu user.
<h2>Scripts</h2>
There are four scripts in the scripts folder:
<li>buildF1.sh
<li>buildF2.sh
<li>startFabric.sh
<li>stopFabric.sh

<strong>buildF1.sh</strong>
Installs the prerequisites go, docker, python and docker-compose.
<strong>buildF2.sh</strong>
Downloads Fabric and starts the network for exercise <i>e2e_cli</i>.
<strong>startFabric.sh</strong>
Starts the network for exercise sample <i>e2e_cli</i>.
<strong>stopFabric.sh</strong>
Stops the network for exercise sample <i>e2e_cli</i>.  This script is called from the cron service daily.

<h2>Install</h2>
Prepare the environment.  Log into your EC2 instance (I chose Ubuntu 16.04). Create new directory <i>scripts</i> under your HOME directory.

Clone the repo and find a a script to install the prerequisites for Fabric as well as build latest version of Fabric:
'source scripts/buidF1.sh'
Use source to invoke this bash. Installs go, python, docker and docker-compose
reboot the EC2.
Verify that user "ubuntu" is in the "docker" group
Run the second script:
'./scripts/buildF2.sh'
