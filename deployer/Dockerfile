FROM node:latest

ADD ./plasma-contracts/contracts /home/node/plasma_framework/build/contracts

ADD ./plasma-contracts/build/db.json /home/node/plasma_framework/build/db.json

ADD ./truffle-config.js /home/node/plasma_framework/truffle-config.js

RUN chown -R node /home/node/plasma_framework

USER node

WORKDIR /home/node

ENV NPM_CONFIG_PREFIX=/home/node/.npm-global

ENV PATH=$PATH:/home/node/.npm-global/bin

RUN npm install -g truffle

CMD cd plasma_framework && sleep 20s  && truffle migrate --verbose-rpc --reset
