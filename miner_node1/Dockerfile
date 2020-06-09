FROM ethereum/client-go:alltools-stable

ADD ./datadir1 ./datadir

ADD ./password.txt ./password.txt

ENV account=""
ENV bootnodes=""

CMD sleep 10s && geth --datadir datadir/ --bootnodes $bootnodes  --networkid "1337" --gasprice "0" --datadir ./datadir --unlock "0,1,2" --password password.txt --mine --minerthreads=1 --etherbase $account --nat extip:`hostname -i` --syncmode="full"  --allow-insecure-unlock --rpc --rpcaddr "0.0.0.0" --rpcapi "eth,web3,net,admin,debug,db" --rpccorsdomain "*" --rpcvhosts=* --miner.gastarget 7500000

EXPOSE 30303
EXPOSE 8545
