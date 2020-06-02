FROM ethereum/client-go:alltools-stable

ADD ./genesis.json ./genesis.json

RUN geth --datadir ./datadir init genesis.json

ADD ./accounts ./datadir/keystore

ADD ./password.txt ./password.txt

ENV account=""
ENV bootnodes=""

CMD geth --bootnodes $bootnodes  --networkid "900991" --gasprice "0" --datadir ./datadir --unlock $account --password password.txt --mine --verbosity=4 --etherbase $account --nat extip:`hostname -i`
