# Продуктовый помощник

![Yamdb Workflow Status](https://github.com/div-ice/foodgram-project-react/actions/workflows/main.yml/badge.svg?branch=master&event=push)

[![Python](https://img.shields.io/badge/-Python-464646?style=flat-square&logo=Python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/-Django-464646?style=flat-square&logo=Django)](https://www.djangoproject.com/)
[![Django REST Framework](https://img.shields.io/badge/-Django%20REST%20Framework-464646?style=flat-square&logo=Django%20REST%20Framework)](https://www.django-rest-framework.org/)
[![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-464646?style=flat-square&logo=PostgreSQL)](https://www.postgresql.org/)
[![Nginx](https://img.shields.io/badge/-NGINX-464646?style=flat-square&logo=NGINX)](https://nginx.org/ru/)
[![gunicorn](https://img.shields.io/badge/-gunicorn-464646?style=flat-square&logo=gunicorn)](https://gunicorn.org/)
[![docker](https://img.shields.io/badge/-Docker-464646?style=flat-square&logo=docker)](https://www.docker.com/)
[![GitHub%20Actions](https://img.shields.io/badge/-GitHub%20Actions-464646?style=flat-square&logo=GitHub%20actions)](https://github.com/features/actions)
[![Yandex.Cloud](https://img.shields.io/badge/-Yandex.Cloud-464646?style=flat-square&logo=Yandex.Cloud)](https://cloud.yandex.ru/)

## Описание

«Продуктовый помощник»: это ресурс, на котором пользователи публикуют рецепты. Авторизованные пользователи добавляют чужие рецепты в избранное и подписываются на публикации других авторов. Также можно добавить рецепты в корзину для того чтобы можно было скачать список ингридиентов для покупки.

## Подготовка и запуск проекта
### Склонировать репозиторий на локальную машину:
```
git clone https://github.com/Div-ICE/foodgram-project-react
```
## Для работы с удаленным сервером (на ubuntu):
* Выполните вход на свой удаленный сервер

* Установите docker на сервер:
```
sudo apt install docker.io 
```
* Установите docker-compose на сервер:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
* Локально отредактируйте файл infra/nginx/default.conf и в строке server_name впишите свой IP
* Скопируйте файлы docker-compose.yml и nginx.conf из директории infra на сервер:
```
scp docker-compose.yml <username>@<host>:/home/<username>/docker-compose.yml
scp nginx.conf <username>@<host>:/home/<username>/nginx/default.conf
```

### Запуск проекта в Docker compose

- Запуск docker compose:

```bash
docker-compose up -d --build
```  

- Сбор статики:

```bash
docker-compose exec backend python manage.py collectstatic --no-input
```  

- Миграции:

```bash
docker-compose exec backend python manage.py migrate
```

- Запуск процесса загрузки ингредиентов и тегов (папки дата внутри backend):

```bash
docker-compose exec backend python manage.py load_ingrs
```

```bash
docker-compose exec backend python manage.py load_tags
```

- Создание суперпользователя:

```bash
docker-compose exec backend python manage.py createsuperuser
```

### Шаблон наполнения .env (не включен в текущий репозиторий) расположенный по пути infra/.env

```python
DB_ENGINE=django.db.backends.postgresql 
DB_NAME=postgres 
POSTGRES_USER=postgres 
POSTGRES_PASSWORD=postgres 
DB_HOST=db 
DB_PORT=5432 
```
Данный сайт доступен по адресу http://yatube.sytes.net/
