# api_yamdb

![Git-Hub Actions](https://github.com/kirenger/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
### Описание

Проект YaMDb собирает отзывы пользователей на произведения.

Ключевые моменты:

Применены вьюсеты.

Для аутентификации использованы JWT-токены.

У неаутентифицированных пользователей доступ к API только на чтение.


### Установка

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/kirenger/api_yamdb.git
```
Перейти в папку infra

```
cd infra
```

Запустить docker-compose.yaml (при установленном и запущенном Docker)

```
sudo docker compose up -d --build
```

Создаем миграции

```
sudo docker compose exec web python manage.py makemigrations
```

Запустили миграции

```
sudo docker compose exec web python manage.py migrate
```

Создаем суперюзера

```
sudo docker compose exec web python manage.py createsuperuser
```

Собираем статику

```
sudo docker compose exec web python manage.py collectstatic --no-input
```

Проверяем работоспособность приложения:

```
 http://localhost/admin/
```

Теперь наполните БД тестовыми данными.

Можете сделать резервную копию БД командой

```
sudo docker compose exec web python manage.py dumpdata > fixtures.json
```

Подгрузите данные БД из директории infra\docker-compose.yaml:

```
sudo docker compose exec web python manage.py loaddata fixtures.json
```

### Примеры

Документация API

```
localhost:8000/redoc
```
