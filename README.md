## Запуск проекта из репозитория в GitHub

Клонируем себе репозиторий: 

```bash 
git clone git@github.com:rete11/kittygram_final.git
```

Выполняем запуск:

```bash
sudo docker compose -f docker-compose.yml up
```

## После запуска: Миграции, сбор статистики

После запуска нужно выполнить сбор статистики и миграцию для бэкенда. Статистика фронтенда собирается во время запуска контейнера, после чего он останавливается. 

```bash
sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py migrate

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py collectstatic

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend cp -r /app/collected_static/. /static/static/
```

теперь проект доступен на: 

```
http://localhost:9000/
```

## Описание переменных окружения

Ниже пример файла .env c переменными окружения, необходимыми для запуска приложения

```bash
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_HOST=db
DEBUG=False
SECRET_KEY=django_secret_key_example
```