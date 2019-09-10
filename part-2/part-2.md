# Part 2

## 2.1
Docker-compose:
```
version: '3.7'
services:
  logger:
    image: devopsdockeruh/first_volume_exercise
    volumes:
      - type: bind
        source: ./logs.txt
        target: /usr/app/logs.txt
```

## 2.2
Docker-compose:
```
version: '3.7'
services:
  ports:
    image: devopsdockeruh/ports_exercise
    ports:
    - "80:80"
```
