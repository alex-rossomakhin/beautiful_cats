#  Beautiful cats - социальная сеть для размещение фотографий домашних животных.

## Описание 

Проект, где пользователю доступна регистрация, добавление фотографий и описания достижений котов. Так же есть возможность просматривать фотографии других котов.
Запуск проекта происходит через Docker

## Технологии

* Python 3.9
* Django==3.2.3
* djangorestframework==3.12.4
* nginx
* gunicorn==20.1.0
* djoser==2.1.0

## Запуск проекта

Скачайте [docker-compose.yml](https://github.com/alex-rossomakhin/beautiful_cats/blob/main/docker-compose.production.yml) из репозитория 

Создайте файл .env

```bash
touch .env
```

Создайте файл с переменными окружения

```bash
POSTGRES_DB=<БазаДанных>
POSTGRES_USER=<имя пользователя>
POSTGRES_PASSWORD=<пароль>
DB_NAME=<имя БазыДанных>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=<ключ Django>
DEBUG=<DEBUG True/False>
ALLOWED_HOSTS=<разрешенные хосты>
```
Запустите Dockercompose

```bash
sudo docker compose -f docker-compose.yml pull
sudo docker compose -f docker-compose.yml down
sudo docker compose -f docker-compose.yml up -d
```

Сделайте миграции и соберите статику

```bash
sudo docker compose -f docker-compose.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/ 
```

## Автор

[Alexey Rossomakhin](https://github.com/alex-rossomakhin)
