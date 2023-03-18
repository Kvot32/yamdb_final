# Привет! 

### Описание

Приложение YaMDB позволяет оставлять отзывы о произведениях в различных категориях и жанрах, а также оставлять оценки произведениям и комментировать существующие отзывы.

### Технологии

Для разработки проекта применялись следующие технологии:

#### *Python*
#### *Django*
#### *SQLite3*
#### *Postgres*
#### *API DRF*
#### *GitHub*
#### *Docker* и *Docker Actions*
#### и сотни страниц с информацией в интернете)))

### Процесс регистрации новых пользователей:
1. Пользователь отправляет запрос с параметрами *email* и *username* на **/api/v1/auth/signup/**.  
2. Сервис YaMDB отправляет письмо с кодом подтверждения (confirmation_code) на указанный email-адрес.
3. Пользователь отправляет запрос с параметрами *username* и *confirmation_code* на эндпоинт **/api/v1/auth/token/**, в ответе на запрос ему приходит *token* (JWT-токен).
После регистрации и получения токена пользователь может отправить PATCH-запрос на **/users/me/** и заполнить поля в своём профайле (описание полей — в документации).

### Процесс установки:

 Клонируем репозиторий и переходим в него через терминал:

 ```$ git clone https://github.com/OvcharukDmitrij/yamdb_final.git```
 
 ```$ cd yamdb_final```

 ### Настройка переменных окружения:

 В корневой папке проекта необходимо создать файл .env и указать в нем переменные окружения.

#### Пример: 
```DB_ENGINE=django.db.backends.postgresql``` - указываем, что работаем с postgresql

```DB_NAME=postgres``` - имя базы данных

```POSTGRES_USER=postgres``` - логин для подключения к базе данных

```POSTGRES_PASSWORD=postgres``` - пароль для подключения к БД (установите свой)

```DB_HOST=db``` - название сервиса (контейнера)

```DB_PORT=5432``` - порт для подключения к БД 
 
### Команды для запуска docker-compose:

```docker-compose up -d --build``` - сборка контейнеров и их запуск

``` docker-compose exec web python manage.py migrate``` - выполнение миграций

```docker-compose exec web python manage.py createsuperuser``` - создание суперюзера

```docker-compose exec web python manage.py collectstatic --no-input``` - сбор статических файлов
 

### Процесс заполнения БД из CSV-файлов

Открыть файл ```api_yamdb/reviews/management/commands/load_data.py```

Указать имя модели: ```MODEL = ModelName ```

Указать имя csv файла: ```DATA_FILE = 'file_name.csv'```

Выполнить команду: ```python3 manage.py load_data```

### Основные запросы API

Регистрация нового пользователя POST```/api/v1/auth/signup/```

Получение токена POST ```/api/v1/auth/token/```

Получение списка произведений GET ```/api/v1/titles/```

Получение конкретного произведения GET ```/api/v1/titles/{titles_id}/```

Получение списка всех отзывов GET ```/api/v1/titles/{title_id}/reviews/```

Получение списка всех комментариев GET ```/api/v1/titles/{title_id}/reviews/{review_id}/comments/```

### Workflow

![This is an image](https://github.com/Kvot32/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master&event=push)


