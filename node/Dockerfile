FROM ethereum/client-go:alltools-stable

ADD ./genesis.json ./genesis.json

RUN geth --datadir ./datadir init genesis.json

ADD ./accounts ./datadir/keystore

ADD ./static-nodes.json ./datadir/static-nodes.json

ADD ./password.txt ./password.txt

ENV account=""
ENV bootnodes=""

CMD sleep 10s && geth --bootnodes $bootnodes  --networkid "9010100" --gasprice "0" --datadir ./datadir --unlock $account --password password.txt --mine --minerthreads=1 --etherbase $account --nat extip:`hostname -i` --syncmode="full"  --allow-insecure-unlock --rpc --rpcaddr "0.0.0.0" --rpcapi "eth,web3,net,admin,debug,db" --rpccorsdomain "*"

EXPOSE 30303
EXPOSE 8545
