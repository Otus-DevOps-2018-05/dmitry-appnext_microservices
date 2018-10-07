# dmitry-appnext_microservices
dmitry-appnext microservices repository

- [Docker-1](#docker-1)  [![Build Status](https://travis-ci.com/Otus-DevOps-2018-05/dmitry-appnext_microservices.svg?branch=docker-1)]
- [Docker-2](#docker-2)  [![Build Status](https://travis-ci.com/Otus-DevOps-2018-05/dmitry-appnext_microservices.svg?branch=docker-2)]
- [Docker-2](#docker-3)  [![Build Status](https://travis-ci.com/Otus-DevOps-2018-05/dmitry-appnext_microservices.svg?branch=docker-3)]


# DOCKER - 3

## Запуск приложения

docker volume create reddit_db
docker kill $(docker ps -q)
docker run -d -v reddit_db:/data/db --network=reddit --network-alias=post_db --network-alias=comment_db mongo:latest && \
docker run -d --network=reddit --network-alias=post dmitryappnext/post:1.0 && \
docker run -d --network=reddit --network-alias=comment dmitryappnext/comment:1.0 &&\
docker run -d --network=reddit -p 9292:9292 dmitryappnext/ui:2.0

## Задание со *: запустить контейнеры с другими сетевыми алиасами

docker run -d --network=reddit --network-alias=post_db2 --network-alias=comment_db2 mongo:latest
docker run -d --network=reddit --network-alias=post2 --env POST_DATABASE_HOST=post_db2  dmitryappnext/post:1.0
docker run -d --network=reddit --network-alias=comment2 --env COMMENT_DATABASE_HOST=comment_db2 dmitryappnext/comment:1.0
docker run -d --network=reddit -p 9292:9292 --env POST_SERVICE_HOST=post2 --env COMMENT_SERVICE_HOST=comment2 dmitryappnext/ui:1.0

# DOCKER - 2

## Что было сделано

 - установлена docker-machine
```
docker-machine create --driver google \
--google-machine-image https://www.googleapis.com/compute/v1/
projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts \
--google-machine-type n1-standard-1 \
--google-zone europe-west1-b \
docker-host
```
- Собран образ докер-контейнера с установленным приложением reddit на удаленной машине

- Образ докер-контейнера был загружен в docker registry
cmd: docker push dmitryappnext/otus-reddit:1.0
