FROM ethereum/client-go:alltools-stable

ADD ./genesis.json ./genesis.json

RUN geth --datadir ./datadir init genesis.json

ADD ./accounts ./datadir/keystore

ADD ./password.txt ./password.txt

CMD geth --datadir ./datadir --unlock 0 --password password.txt console
