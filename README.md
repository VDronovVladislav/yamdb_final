### Проект yamdb_final.
Веб-проект c отзывами пользователей на произведения.
Произведения делятся на категории и жанры. Администратор может добавлять произведения, категории и жанры.
Пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти, из пользовательских оценок формируется усреднённая оценка произведения — рейтинг.
## Стек:
Стек: Django,Gunicorn, nginx, Rest API (DRF), PostgreSQL, Djoser, Simple JWT, Docker, CI/CD (GitHub
Actions)
## инcтрукция по запуску:

  
Клонировать репозиторий и перейти в него в командной строке:
  
```
git@github.com:VDronovVladislav/yamdb_final.git
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

Адреса для проверки проекта:
```
http://84.201.129.205/api/v1/
http://84.201.129.205/admin/
http://84.201.129.205/redoc/
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
