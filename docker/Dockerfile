FROM node:22-alpine

ENV NODE_PATH /opt/node_modules

WORKDIR /workspace

# RUN apt-get -y update && apt-get install -y --no-install-recommends \
#         git \
#     && apt-get -y clean
RUN apk update && apk add git bash


RUN npm init --yes \
    && npm install -g zenn-cli@latest \
    && npx zenn install
