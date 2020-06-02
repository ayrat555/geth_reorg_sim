FROM ethereum/client-go:alltools-stable

ADD ./genesis.json ./genesis.json

RUN geth --datadir ./datadir init genesis.json

ADD ./accounts ./datadir/keystore

ADD ./password.txt ./password.txt

ENV account="0"
ENV bootnodeId=""
ENV bootnodeIp=""

CMD geth --bootnodes "enode://$bootnodeId@$bootnodeIp:30301" --networkid "900" --datadir ./datadir --unlock $account --password password.txt --mine --verbosity=4
