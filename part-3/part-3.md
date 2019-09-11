# Part 3

## 3.1

I was already using node:alpine images for these as the base so I am not sure
how much of the image size can be shaved off by optimising the dockefile as such.

Maybe a minimized js bundlecould be created for both of these images and that would reduce the image size further. This could be achieved using multi-stage builds in Docker.

### Backend
- Original ( From 1.11 ) size: 135MB

- Ubuntu reference size from instructions:  351MB

```
FROM node:10.16.3-alpine

WORKDIR /usr/app

COPY . .

RUN npm install

EXPOSE 8000

ENTRYPOINT ["npm", "start"]
```

### Frontend
- Original ( from 1.10 ) size: 232MB
- Ubuntu reference side from instructions:  351MB

```
FROM node:10.16.3-alpine

WORKDIR /usr/app

COPY . .

RUN npm install

EXPOSE 5000

ENTRYPOINT ["npm", "start"]
```

## 3.2

### Unoptimized:
Size: 761MB
Dockerfile:
```
FROM ubuntu:16.04

ARG DEBIAN_FRONTEND=noninteractive

RUN echo DEBIAN_FRONTEND

RUN apt-get update

RUN apt-get install -y rtmpdump wget ffmpeg python3-dev python3-setuptools \
    python3-pip python3-crypto python3-requests python3-lxml \
    php-cli php-curl php-xml php-bcmath

RUN pip3 install --user --upgrade yle-dl

RUN mkdir /usr/downloads

ENTRYPOINT export PATH=$PATH:$HOME/.local/bin && yle-dl -o /usr/downloads/podcast.mp3 https://areena.yle.fi/1-50248693
```
