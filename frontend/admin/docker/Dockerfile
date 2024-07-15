FROM --platform=linux/amd64 node:20.15.1

ARG LANG
ARG TZ

ENV ROOT=/admin
ENV LANG=${LANG}
ENV TZ=${TZ}

RUN mkdir -p ${ROOT}/src
WORKDIR ${ROOT}/src

RUN npm i -g pnpm

COPY src/package.json ./package.json
COPY src/pnpm-lock.yaml ./pnpm-lock.yaml

RUN pnpm i

COPY . ${ROOT}
