FROM ethereum/client-go:alltools-stable

ADD ./bootnode.key ./bootnode.key

CMD bootnode -nodekey bootnode.key

EXPOSE 30303/udp