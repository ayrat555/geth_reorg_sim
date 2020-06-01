FROM ethereum/client-go:alltools-stable

ADD ./genesis.json ./genesis.json

RUN geth --datadir ./datadir init genesis.json
