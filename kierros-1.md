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
