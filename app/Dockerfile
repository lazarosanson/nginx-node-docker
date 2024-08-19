FROM node:20.15.1-alpine

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

ENV DOCKERIZE_VERSION v0.8.0

RUN apk update --no-cache \
    && apk add --no-cache wget openssl \
    && wget -O - https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz | tar xzf - -C /usr/local/bin \
    && apk del wget

COPY . .

EXPOSE 3000

ENTRYPOINT [ "node", "index.js" ]