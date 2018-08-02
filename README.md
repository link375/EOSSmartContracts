# EOS Smart Contracts
Collection of EOS smart contracts and resources

# Development environment setup & requirements

Ubuntu 18.04

20GB Storage

7GB RAM

Git / Docker

# BUILD FROM SOURCE

> git clone https://github.com/EOSIO/eos --recursive

> git checkout tags/dawn-v4.2.0

> git submodule update --init --recursive

> ./eosio_build.sh

> export PATH=${HOME}/opt/mongodb/bin:$PATH
	/home/user/opt/mongodb/bin/mongod -f /home/user/opt/mongodb/mongod.conf &
	cd /home/user/eos/build; make test

> sudo make install

# DOCKER INSTALL

https://developers.eos.io/eosio-nodeos/docs/docker-quickstart

> sudo apt install docker.io

> sudo su

> docker pull eosio/eos-dev

> docker run --rm --name eosio -d -p 8888:8888 -p 9876:9876 -v /tmp/work:/work -v /tmp/eosio/data:/mnt/dev/data -v /tmp/eosio/config:/mnt/dev/config eosio/eos-dev  /bin/bash -c "nodeos -e -p eosio --plugin eosio::wallet_api_plugin --plugin eosio::wallet_plugin --plugin eosio::producer_plugin --plugin eosio::history_plugin --plugin eosio::chain_api_plugin --plugin eosio::history_api_plugin --plugin eosio::http_plugin -d /mnt/dev/data --config-dir /mnt/dev/config --http-server-address=0.0.0.0:8888 --access-control-allow-origin=* --contracts-console --http-validate-host=false"

> docker logs --tail 10 eosio

Login to docker container

> docker exec -it eosio bash

Stop EOS

> bash docker stop eosio

# CLEOS - CLI (Docker)

https://developers.eos.io/eosio-nodeos/docs/cleos-overview

create alias to cleos

> sudo su

> alias cleos='docker exec -it eosio /opt/eosio/bin/cleos -u http://0.0.0.0:8888 --wallet-url http://0.0.0.0:8888'

> cleos --help

# KEOSD - Manages wallets

Wallets: (encrypted) stores multiple key-pairs

Account: On-chain identifier tied to a public key


# Create wallet

https://developers.eos.io/eosio-nodeos/docs/learn-about-wallets-keys-and-accounts-with-cleos

Create wallet - returns pwd

> cleos create wallet -n <name>

View wallets - * = unlocked

> cleos wallet list

Lock wallet

> cleos wallet -n <name> lock

Unlock wallet

> cleos wallet -n <name> unlock


# Create and import key-pairs

Create a keypair

> cleos create key

Import the keypair to your wallet - make sure your wallet is unlocked

> cleos wallet import <keynumber>

Verify import worked

> cleos wallet keys

View public/private keypairs in the wallet

> cleos wallet private_keys --password

# Backup wallets

> cd ~/eos-wallet && ls 

If you're using docker the wallet will be in the /tmp directory

> cd /tmp/eosio/data/

# Creating an account

