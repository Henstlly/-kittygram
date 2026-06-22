# Kittygram

Проект для публикации карточек котиков с достижениями.

## Стек

- **Backend**: Django 5, Django REST Framework, Djoser
- **Frontend**: React 17
- **БД**: PostgreSQL 15
- **Инфраструктура**: Docker, Docker Compose, Nginx, Gunicorn

## Запуск через Docker

1. Клонировать репозиторий:
   ```bash
   git clone https://github.com/Henstlly/-kittygram.git
   cd -kittygram
   ```

2. Создать файл `.env` по образцу `.env.example`:
   ```bash
   cp .env.example .env
   ```

3. Запустить сборку и контейнеры:
   ```bash
   docker compose up --build -d
   ```

4. Выполнить миграции:
   ```bash
   docker compose exec backend python manage.py migrate
   ```

5. Собрать статику:
   ```bash
   docker compose exec backend python manage.py collectstatic
   ```

6. Создать суперпользователя:
   ```bash
   docker compose exec backend python manage.py createsuperuser
   ```

7. Открыть в браузере: [http://localhost:8080](http://localhost:8080)

8. Остановить проект:
   ```bash
   docker compose down
   ```

## Локальный запуск (без Docker)

### Backend
```bash
cd kittigram_backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py collectstatic
python manage.py createsuperuser
python manage.py runserver
```

### Frontend
```bash
cd kittigram_frontend
npm ci
npm run build
```

## Документация API

- **Swagger UI**: [http://localhost:8080/api/docs/swagger/](http://localhost:8080/api/docs/swagger/)
- **ReDoc**: [http://localhost:8080/api/docs/redoc/](http://localhost:8080/api/docs/redoc/)
- **OpenAPI Schema**: [http://localhost:8080/api/schema/](http://localhost:8080/api/schema/)

## Переменные окружения

| Переменная | Значение по умолчанию | Описание |
|------------|----------------------|----------|
| `POSTGRES_USER` | `kittygram_user` | Пользователь БД |
| `POSTGRES_PASSWORD` | `kittygram_password` | Пароль БД |
| `POSTGRES_DB` | `kittygram_db` | Имя БД |
| `DB_HOST` | `db` | Хост БД |
| `DB_PORT` | `5432` | Порт БД |
| `DB_ENGINE` | `django.db.backends.postgresql` | Движок БД |
| `SECRET_KEY` | — | Секретный ключ Django |
| `DEBUG` | `True` | Режим отладки |
| `ALLOWED_HOSTS` | `127.0.0.1,localhost,0.0.0.0` | Разрешённые хосты |
