FROM ethereum/client-go:alltools-stable

ADD ./genesis.json ./genesis.json

RUN geth --datadir ./datadir init genesis.json

ADD ./accounts ./datadir/keystore

ADD ./password.txt ./password.txt

ENV account=""
ENV bootnodeId=""
ENV bootnodeIp=""

CMD geth --bootnodes "enode://$bootnodeId@$bootnodeIp:30303" --networkid "900991" --gasprice "0" --datadir ./datadir --rpc --rpcaddr "0.0.0.0" --rpcapi "eth,web3,net,admin,debug,db" --rpccorsdomain "*" --syncmode="full" --unlock $account --password password.txt --allow-insecure-unlock --nat extip:`hostname -i`

EXPOSE 8545
EXPOSE 30303
