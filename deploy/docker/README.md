
#### Test hardware environment requirements

* Debian/Ubuntu (recommended)

* 20GB storage space

* 4 gb of memory

* X86 architecture

* Static IP Address

* Exposed TCP port 9151

#### how to run PRE workers

* install [Docker](https://docs.docker.com/install/)

* docker pull iandy2233/nulink:latest

* copy the operator/worker's keystore file to the '/path/to/host/machine/directory'

###### run in host machines

* ensure that the host has permissions on the directory to which it is mapped
  `chmod 777 /path/to/host/machine/directory`
* init an ursula config

  `docker run  -p 9151:9151 -v /path/to/host/machine/directory:/code -v /path/to/host/machine/directory:/home/circleci/.local/share/nulink --rm -it iandy2233/nulink nulink ursula init --signer keystore:///code/subpath/to/keystore --eth-provider https://data-seed-prebsc-2-s2.binance.org:8545 --network bsc_testnet --payment-provider https://data-seed-prebsc-2-s2.binance.org:8545 --payment-network bsc_testnet --operator-address  0x7DEff413E415bd2507da4988393d8540a28bf3c6 --max-gas-price 2000`

* start up an ursula
  
  `docker run  -p 9151:9151 -v /path/to/host/machine/directory:/code -v /path/to/host/machine/directory:/home/circleci/.local/share/nulink  --rm -it iandy2233/nulink nulink ursula run --teacher https://8.219.188.70:9151 --no-block-until-ready`


###### or run in the docker container

* run docker container:

  `docker run  -p 9151:9151 -v /path/to/host/machine/directory:/code --rm -it iandy2233/nulink /bin/bash`


* init an ursula config:

  `nulink ursula init --signer keystore:///code/subpath/to/keystore --eth-provider https://data-seed-prebsc-2-s2.binance.org:8545 --network bsc_testnet --payment-provider https://data-seed-prebsc-2-s2.binance.org:8545 --payment-network bsc_testnet --operator-address  0x7DEff413E415bd2507da4988393d8540a28bf3c6 --max-gas-price 2000`


* start up an ursula:

  `nulink ursula run --teacher https://8.219.188.70:9151 --no-block-until-ready`