WillowCoin-v2 [WLLO] 2020 integration/staging tree
===========================================================================================

http://willowcoin.net

What is the WillowCoin [WLLO] Blockchain?
-----------------------------------------

### Overview
WillowCoin is a blockchain project with the goal of offering amazing Staking experience to it's users.
The POS algorithm WillowCoin uses enables it's users to generate passive income without the need of 
buying expensive mining equipments. 

### Blockchain Technology
The WillowCoin [WLLO] Blockchain enables instant payments to anyone, anywhere in the world in a secure manner. 
WillowCoin [WLLO] uses peer-to-peer blockchain technology developed by WillowCoin to operate
with no central authority: managing transactions, execution of contracts, and 
issuing money are carried out collectively by the network. WillowCoin [WLLO] is the name of 
open source software which enables the use of this protocol.

General Specs
----------------
    Block Spacing: 90 seconds
	Stake Min Age: 12 hours
	Anualized POS: 750% 
	Coin Maturity: 60 Blocks
	Maximum Cap: unlimited
	Coin Type: Full POS


BUILD LINUX DEAMON
-----------
### Compiling WillowCoin daemon on Ubunutu 16.04 LTS 
Note: guide should be compatible with other Ubuntu versions from 14.04+

###Set up a swapfile if your system has less than 1.5GB of memory:
```
fallocate -l 2G /swapfile

chown root:root /swapfile

chmod 0600 /swapfile

sudo bash -c "echo 'vm.swappiness = 10' >> /etc/sysctl.conf"

mkswap /swapfile

swapon /swapfile
```
If fallocate doesn’t work, you can use dd if=/dev/zero of=/swapfile bs=1024 count=1024288 instead.

###Initialize swapfile automatically on boot
```
echo '/swapfile none swap sw 0 0' >> /etc/fstab
```
###Install all required dependencies:
```
apt-get update && apt-get upgrade
```
```
apt-get install nano ntp unzip git build-essential libssl-dev libdb-dev libdb++-dev libboost-all-dev libqrencode-dev aptitude && aptitude install miniupnpc libminiupnpc-dev
```
###Pull the source code from github, or upload it yourself:
```
git clone https://github.com/willow-coin/WillowCoin-v2
```
###now you compile the leveldb:
```
cd WillowCoin-v2/src/leveldb

chmod +x build_detect_platform

make clean

make libleveldb.a libmemenv.a
```
###Return to source directory, and compile the daemon:
```
cd ..

make -f makefile.unix
```
###Strip the file to make it smaller, then relocate it:
```
strip WLLOd

cp WLLOd /usr/bin
```
###Now run the daemon:
```
WLLOd
```
###It will return an error, telling you to set up config file in a directory. Now we’ll set up the config file. Note that this is case sensitive.
```
nano ~/.WLLO/WillowCoin-v2.conf
```
###Add the following, save and exit:
```
daemon=1

server=1

rpcuser=(username)

rpcpassword=(strong password)
```
Run WLLOd once more and if you did everything correctly, your daemon is now online! Type WLLOd help for a full list of commands available.
