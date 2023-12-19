[![.github/workflows/main.yml](https://github.com/AvailableNow/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/AvailableNow/kittygram_final/actions/workflows/main.yml)

![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white) ![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)

## Описание проекта

Сайт с возможностью публикации фотографий котов и их достижений.

## Технологии

- Python 3.9
- Django 3.2.3
- Django REST framework 3.12.4
- JavaScript

## Запуск проекта из образов с Docker hub

Для запуска необходимо на создать папку проекта, например `kittygram` и перейти в нее:

```bash
mkdir kittygram
cd kittygram
```

## Заполните файл .env следующими значениями, убедившись, что вы указали актуальные данные:
```.env
SECRET_KEY='указать секретный ключ'
ALLOWED_HOSTS='указать имя или IP хоста'
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_HOST=new_db
DB_PORT=5432
DEBUG=False
```


## В папку проекта скачиваем файл .env и `docker-compose.production.yml` и запускаем его:

```bash
sudo docker compose -f docker-compose.production.yml up
```

Произойдет скачивание образов, создание и включение контейнеров, создание томов и сети.


Выполнить миграции, сбор статики:

```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/

```
Создать суперпользователя, ввести почту, логин, пароль:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```


## Остановка оркестра контейнеров

В окне, где был запуск **Ctrl+С** или в другом окне:

```bash
sudo docker compose -f docker-compose.yml down
```

## Автор Шунин Илья


# Kittygram - социальная сеть для размещение фотографий домашних животных.

## Описание проекта
Проект, где пользователи могут регистрироваться, загружать фотографии кошек с описанием их достижений, а также любоваться на других котов.

## Технологии
•	Python 3.9
•	Django==3.2.3
•	djangorestframework==3.12.4
•	nginx
•	gunicorn==20.1.0
• djoser==2.1.0

## Автор
[@olees-orlenko](https://github.com/olees-orlenko)

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/olees-orlenko/kittygram_final.git 
```

Перейти в корневую директорию
```
cd kittygram_final
```

Создать файл .evn для хранения ключей:

```
SECRET_KEY='указать секретный ключ'
ALLOWED_HOSTS='указать имя или IP хоста'
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432
DEBUG=False
```



#  Как работать с репозиторием финального задания

## Что нужно сделать

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

## Как проверить работу с помощью автотестов

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.

## Чек-лист для проверки перед отправкой задания

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.