FROM node:latest

ADD ./plasma-contracts/contracts /home/node/plasma_framework/build/contracts

ADD ./plasma-contracts/build/db.json /home/node/plasma_framework/build/db.json

RUN chown -R node /home/node/plasma_framework

USER node

WORKDIR /home/node

ENV NPM_CONFIG_PREFIX=/home/node/.npm-global

ENV PATH=$PATH:/home/node/.npm-global/bin

RUN npm install -g truffle
RUN npm install -g json-server

RUN cd plasma_framework && truffle init --force

ADD ./truffle-config.js /home/node/plasma_framework/truffle-config.js

CMD cd plasma_framework && sleep 80s && \
        for i in 1 2 3 4 5; do echo 'Running truffle migration attempt'; \
        truffle migrate --reset && break; \
        done \

EXPOSE 8000
