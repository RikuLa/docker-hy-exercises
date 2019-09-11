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

## 2.3
Docker-compose:
```
version: '3.7'
services:
  frontend:
    build:
      context: ./frontend-example-docker/
      dockerfile: ./Dockerfile-1-12-fe
    ports:
      - "5000:5000"
  backend:
    build:
      context: ./backend-example-docker/
      dockerfile: ./Dockerfile-1-12-be
    ports:
      - "8000:8000"
```

## 2.4
Docker-compose:
```
version: '3.2'
services:
  calculator:
      build: ./calculator
      image: calculator
      ports:
        - 3000:3000
      container_name: calculator
  compute_1:
      build: ./compute
      image: compute
      environment:
        - VIRTUAL_HOST=compute.localtest.me
  compute_2:
      build: ./compute
      image: compute
      environment:
        - VIRTUAL_HOST=compute.localtest.me
  compute_3:
      build: ./compute
      image: compute
      environment:
        - VIRTUAL_HOST=compute.localtest.me
  compute_4:
      build: ./compute
      image: compute
      environment:
        - VIRTUAL_HOST=compute.localtest.me
  load-balancer:
      build: ./load-balancer
      image: load-balancer
      volumes:
        - /var/run/docker.sock:/tmp/docker.sock:ro
      ports:
        - 80:80
      container_name: load-balancer
```

## 2.5
Docker-compose:
```
version: '3.7'
services:
  backend:
    build:
      context: ./backend-example-docker/
      dockerfile: ./Dockerfile-1-12-be
    ports:
      - "8000:8000"
    environment:
      - REDIS=redis
  redis:
    image: redis:latest
  frontend:
    build:
      context: ./frontend-example-docker/
      dockerfile: ./Dockerfile-1-12-fe
    ports:
      - "5000:5000"
```
