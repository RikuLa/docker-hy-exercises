# 1

## 1.1
```
riku-mb:docker-hy koulu$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
59224c7a97ff        nginx               "nginx -g 'daemon of…"   4 minutes ago       Exited (0) 39 seconds ago                       compassionate_kalam
b8d7e0f0e54f        nginx               "nginx -g 'daemon of…"   4 minutes ago       Exited (0) 39 seconds ago                       sharp_boyd
52bea9fababd        nginx               "nginx -g 'daemon of…"   4 minutes ago       Up 4 minutes                80/tcp              quirky_mclaren
```

## 1.2

```
riku-mb:docker-hy koulu$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
```
riku-mb:docker-hy koulu$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```

## 1.3

```
docker run -it devopsdockeruh/pull_exercise

You found the correct password. Secret message is:
"This is the secret message"
```

## 1.4

```
docker run -d devopsdockeruh/exec_bash_exercise

docker exec -it 66a66d5160f2 bash

tail -f ./logs.txt

Sun, 08 Sep 2019 06:24:23 GMT
Sun, 08 Sep 2019 06:24:26 GMT
Sun, 08 Sep 2019 06:24:29 GMT
Sun, 08 Sep 2019 06:24:32 GMT
Secret message is:
"Docker is easy"
```

## 1.5

```
docker run -it ubuntu sh -c 'apt-get update; apt-get --assume-yes install curl;echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
```


## 1.6

Command:
```
docker build -t docker-clock -f Dockerfile-1-6 .
```

Dockerfile (also as a separate file in this directory"):
```
FROM devopsdockeruh/overwrite_cmd_exercise

CMD ["--clock"]
```

## 1.7
Commands:
```
docker build -t curler -f Dockerfile-1-7 .
docker run -it curler
```

Dockerfile:
```
FROM ubuntu

RUN apt-get update && apt-get --assume-yes install curl

CMD echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;
```

## 1.8
```
docker run --mount type=bind,source="$(pwd)"/logs.txt,target=/usr/app/logs.txt devopsdockeruh/first_volume_exercise
```

## 1.9
```
docker run -p 1337:80 devopsdockeruh/ports_exercise
```

## 1.10
Dockerfile:
```
FROM node:10.16.3-alpine

WORKDIR /usr/app

COPY . .

RUN npm install

EXPOSE 5000

ENTRYPOINT ["npm", "start"]
```

## 1.11
Dockerfile:
```
FROM node:10.16.3-alpine

WORKDIR /usr/app

COPY . .

RUN npm install

EXPOSE 8000

ENTRYPOINT ["npm", "start"]

```

Commands:
```
docker build -t 1-11 -f Dockerfile-1-11 .

docker run --mount type=bind,source="$(pwd)"/logs.txt,target=/usr/app/logs.txt -p 8000:8000 1-11

```

## 1.12

### Backend:
#### Commands:
```
docker build -t be -f Dockerfile-1-12-be .
docker run -p 8000:8000 be
```
#### Dockerfile:
```
FROM node:10.16.3-alpine

WORKDIR /usr/app

COPY . .

RUN npm install

EXPOSE 8000

ENV FRONT_URL http://localhost:5000

ENTRYPOINT FRONT_URL=$FRONT_URL npm start
```
### Frontend:
#### Commands:
```
docker build -t fe -f Dockerfile-1-12-fe .
docker run -p 5000:5000 fe
```
#### Dockerfile:
```
FROM node:10.16.3-alpine

WORKDIR /usr/app

COPY . .

RUN npm install

EXPOSE 5000

ENV API_URL http://localhost:8000

ENTRYPOINT API_URL=$API_URL npm start
```

## 1.13
Commands:
```
docker build -t java-spring -f ../docker-hy-exercises/part-1/Dockerfile-1-13 .
docker run -p 8080:8080 java-spring
```

Dockerfile:
```
FROM openjdk:12-alpine

WORKDIR /usr/app

COPY . .

RUN ./mvnw package

EXPOSE 8080

ENTRYPOINT java -jar ./target/docker-example-1.1.3.jar
```

## 1.14
Commands:
```
docker build -t rails -f ../docker-hy-exercises/part-1/Dockerfile-1-14 .
docker run -p 3000:3000 rails
```

Dockerfile:
```
FROM ruby:2.6.0

RUN apt-get update
RUN apt-get install --assume-yes nodejs

WORKDIR /usr/app

COPY . .

RUN bundle install

RUN rails db:migrate

EXPOSE 3000

ENTRYPOINT RAILS_LOG_TO_STDOUT=true rails s
```

## 1.15

SKIPPED

## 1.16

Heroku url:
```
https://heroku-test-docker-rl.herokuapp.com/
```

## 1.17
Dockerfile:
```
FROM ubuntu:cosmic

RUN apt-get update

RUN apt-get install --assume-yes git curl

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash

RUN apt-get install -y nodejs

RUN npm install -g yarn
```
Base of the image is Ubuntu Cosmic, because it is good for general development work. Installs a development environment for Node applications. Yarn is added as a faster alternative for default node package manager (NPM) and git is needed for version control. This could be a typical environment for frontend development for
example.
