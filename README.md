# Задание 2. Request-Reply - NATS
Реализован микросервис api, основная задача которого - принимать запросы от клиента и направлять их в микросервис storage с помощью системы обмена сообщениями NATS. В качестве примера взаимодействия микросервисов необходимо реализован тестовый маршрут GET api/test, который публикует сообщение в NATS.

Реализован микросервис storage, основная задача которого - принимать запросы от микросервиса api и вызывать соответствующие методы репозитория. В качестве примера взаимодействия микросервисов, создана подписка на сообщение, опубликованное в микросервисе api и указан тестовый обработчик, который вызывает метод find репозитория test.

### Зависимости
Для работы проекта необходимо наличие Docker и двух запущенных контейнеров.

**NATS**
```
docker run -d --name nats -p 4222:4222 -p 6222:6222 -p 8222:8222 nats
```

**Postgres**
```
$ docker run --name postgres -e POSTGRES_PASSWORD=yourpassword -p 5432:5432 -d postgres
```
### Запуск
Для запуска следует установить зависимости

**Общие. В корне проекта**
```
npm ci
```

**Зависимости api**
```
cd ./packages/api
npm ci
```
**Зависимости storage**
```
cd ..
cd /storage/api
npm ci
```
В корне проекта выполнить
```
npm start
```

#### Пример запроса:

GET / HTTP/1.1
Host: localhost:5000/api/test
