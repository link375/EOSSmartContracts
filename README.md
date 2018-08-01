# EOS Smart Contracts
Collection of EOS smart contracts and resources

# Development environment setup & requirements

Ubuntu 18.04

20GB Storage

7GB RAM

Git / Docker

# DOCKER INSTALL

https://developers.eos.io/eosio-nodeos/docs/docker-quickstart

> sudo apt install docker.io

> sudo su

> docker pull eosio/eos-dev

> docker run --rm --name eosio -d -p 8888:8888 -p 9876:9876 -v /tmp/work:/work -v /tmp/eosio/data:/mnt/dev/data -v /tmp/eosio/config:/mnt/dev/config eosio/eos-dev  /bin/bash -c "nodeos -e -p eosio --plugin eosio::wallet_api_plugin --plugin eosio::wallet_plugin --plugin eosio::producer_plugin --plugin eosio::history_plugin --plugin eosio::chain_api_plugin --plugin eosio::history_api_plugin --plugin eosio::http_plugin -d /mnt/dev/data --config-dir /mnt/dev/config --http-server-address=0.0.0.0:8888 --access-control-allow-origin=* --contracts-console --http-validate-host=false"

> docker logs --tail 10 eosio

# Login to docker container

> docker exec -it eosio bash

# Stop EOS

> bash docker stop eosio

# CLEOS - CLI

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



