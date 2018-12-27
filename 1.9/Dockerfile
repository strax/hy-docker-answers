FROM node:stretch

RUN node --version

RUN apt-get update && apt-get install -y zsh git man

ARG PURESCRIPT_VERSION=v0.12.1
ARG PURESCRIPT_BIN_SHA1=8b93532f0668a58c1c42b816c5fff11962fd8197

WORKDIR /tmp

RUN wget https://github.com/purescript/purescript/releases/download/${PURESCRIPT_VERSION}/linux64.tar.gz -O purescript-${PURESCRIPT_VERSION}.tar.gz \
    && echo "${PURESCRIPT_BIN_SHA1} purescript-${PURESCRIPT_VERSION}.tar.gz" | sha1sum -c - \
    && tar -xf purescript-${PURESCRIPT_VERSION}.tar.gz -C /opt/ \
    && rm -f purescript-${PURESCRIPT_VERSION}.tar.gz

ENV PATH /opt/purescript:$PATH

RUN npm install -g bower pulp

RUN purs --version


WORKDIR /home/node/psci-session
RUN chown -R node /home/node
USER node
RUN pulp init

CMD pulp psci
