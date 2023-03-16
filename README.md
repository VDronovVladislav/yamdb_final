### Проект yamdb_final:
## инcтрукция по запуску:

  
Клонировать репозиторий и перейти в него в командной строке:
  
```
git@github.com:VDronovVladislav/infra_sp2.git
```

Отредактировать .env файл. Шаблон наполнения:
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql

DB_NAME=postgres # имя базы данных

POSTGRES_USER=postgres # логин для подключения к базе данных

POSTGRES_PASSWORD=password # пароль для подключения к БД (установите свой)

DB_HOST=db # название сервиса (контейнера)

DB_PORT=5432 # порт для подключения к БД
```
  
Запустить docker-compose командой:
```
docker-compose up -d
```

Выполнить миграции приложений в web-контейнере:
  
```
docker-compose exec web python manage.py makemigrations users
```
```
docker-compose exec web python manage.py makemigrations reviews
```
```
docker-compose exec web python manage.py migrate
```

Создать суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
Собрать статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```

Проект доступен по адресу:
```
http://localhost/
```

Для заполнения базы данными поочередно и в таком порядке выполнить команды:
```
docker-compose exec web python manage.py load_users_data
docker-compose exec web python manage.py load_genre_data
docker-compose exec web python manage.py load_category_data
docker-compose exec web python manage.py load_titles_data
docker-compose exec web python manage.py load_genre_title_data
docker-compose exec web python manage.py load_review_data
docker-compose exec web python manage.py load_comments_data
```

Остановить контейнеры можно командой:
```
docker-compose down -v
```

Лиценция:
```
MIT License
```

Workflow:
> ![workflow](https://github.com/VDronovVladislav/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Об авторе:
Привет. Меня зовут Дронов Владислав. Студент 17+ когорты направления Python-разработки.
За весь проект не было сломано ни одной клавиатуры.
