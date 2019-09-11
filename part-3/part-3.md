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
