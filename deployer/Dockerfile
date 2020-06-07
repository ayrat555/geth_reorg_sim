FROM node:latest

ADD ./plasma-contracts/contracts /home/node/plasma_framework/build/contracts

RUN chown -R node /home/node/plasma_framework

USER node

WORKDIR /home/node

ENV NPM_CONFIG_PREFIX=/home/node/.npm-global

ENV PATH=$PATH:/home/node/.npm-global/bin

RUN npm install -g truffle

RUN cd plasma_framework && truffle init --force && truffle migrate
