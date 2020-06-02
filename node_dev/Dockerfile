FROM ethereum/client-go:alltools-stable

ADD ./genesis.json ./genesis.json

RUN geth --datadir ./datadir init genesis.json

ENV bootnodeId=""
ENV bootnodeIp=""

CMD geth --bootnodes "enode://$bootnodeId@$bootnodeIp:30301" --networkid "900" --datadir ./datadir --rpc --rpcaddr "0.0.0.0" --rpcapi "eth,web3,net,admin,debug,db" --rpccorsdomain "*" --syncmode="full"

EXPOSE 8545
EXPOSE 30303
