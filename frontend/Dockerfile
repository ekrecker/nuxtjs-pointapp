FROM node:16-alpine

RUN mkdir /app
WORKDIR /app

ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

RUN apk update && \
    apk upgrade && \
    apk add git make g++ && \
    npm add -g @vue/cli @vue/cli-init

COPY . /app
WORKDIR /app/app
EXPOSE 3000
