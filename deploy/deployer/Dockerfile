FROM node:10-alpine

RUN apk update && apk add make git g++ python

RUN git clone https://github.com/omgnetwork/plasma-contracts /home/node/plasma-contracts/

RUN chown -R node /home/node/plasma-contracts

USER node

WORKDIR /home/node

ENV NPM_CONFIG_PREFIX=/home/node/.npm-global

ENV PATH=$PATH:/home/node/.npm-global/bin

ENV DEPLOYER_PRIVATEKEY=d885a307e35738f773d8c9c63c7a3f3977819274638d04aaf934a1e1158513ce
ENV MAINTAINER_PRIVATEKEY=e91a81533b61281b920784e0bad25c19b3671639d86e643bf1e60ec8c2244f8a
ENV AUTHORITY_PRIVATEKEY=7f30f140fd4724519e5017c0895f158d68bbbe4a81c0c10dbb25a0006e348807
ENV REMOTE_URL=http://172.25.0.102:8545
ENV DEPLOY_TEST_CONTRACTS=true
ENV MIN_EXIT_PERIOD=120

RUN npm install -g truffle
RUN npm install -g json-server
RUN cd /home/node/plasma-contracts/plasma_framework && npm install

CMD cd ./plasma-contracts/plasma_framework && sleep 80s && \
        for i in 1 2 3 4 5; do echo 'Running truffle migration attempt'; \
        truffle migrate --network remote && break; \
        done

EXPOSE 8000
