# dmitry-appnext_microservices
dmitry-appnext microservices repository

- [Docker-1](#docker-1)  [![Build Status](https://travis-ci.com/Otus-DevOps-2018-05/dmitry-appnext_microservices.svg?branch=docker-1)]
- [Docker-2](#docker-2)  [![Build Status](https://travis-ci.com/Otus-DevOps-2018-05/dmitry-appnext_microservices.svg?branch=docker-2)]

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
