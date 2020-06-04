# Geth chain reorganization sim

This repo is meant to be used for testing some assumptions against reorgs in the chain.

# Prerequisites

- [pumba](https://github.com/alexei-led/pumba)
- docker
- docker-compose

# Usage

The docker-compose starts a chain with two nodes with `ethash` consensus algorithm. The etherbase of the first node is `0x8404AFE09D770271c935019F9f774CBA2bea291d`, the etherbase of the second node is `0x2DEd039Be2c7e09Ea244F872003C8d50D9CF9F02`.

Both nodes expose JSON RPC API:

- http://localhost:9000 - the first node
- http://localhost:9001 - the second node

They are load balanced by nginx which runs on http://localhost:80

Both nodes have three addresses unlocked:

- 0x2ded039be2c7e09ea244f872003c8d50d9cf9f02
- 0x8404afe09d770271c935019f9f774cba2bea291d
- 0xc8e2d04f0c3a825aae21d54d67cb65a63a154c12

To trigger reorgs:

- Choose one of the three account to submit transactions with
- Pause the first node with `pumba pause -d 100s node-1`
- While the first node is paused, submit transactions to the second node using json rpc api
- Pause the second node with `pumba pause -d 100s node-2`
- Unpause the first node
- Submit transactions to the first node using json rpc api
- Now the first and the second nodes have different sets of blocks and transactions. Unpause the second node - reorganization will be found.
