# API для Yatube

## Описание
`api-final-yatube-ad` — это учебный backend-проект на Django REST Framework для социальной платформы Yatube.
API позволяет:
- получать список публикаций и отдельные публикации;
- создавать, редактировать и удалять свои публикации;
- работать с комментариями к публикациям;
- просматривать сообщества (группы);
- подписываться на авторов и искать подписки;
- проходить аутентификацию через JWT-токены.

Проект реализован по принципу «документация как ТЗ»: спецификация доступна в формате Redoc по адресу `/redoc/` после запуска сервера.

## Технологии
- Python 3.10+
- Django 3.2
- Django REST Framework
- SimpleJWT
- django-filter
- SQLite (по умолчанию)

## Установка и запуск
1. Клонируйте репозиторий:
```bash
git clone <URL_ВАШЕГО_РЕПОЗИТОРИЯ>
cd api-final-yatube-ad
```

2. Создайте и активируйте виртуальное окружение:
```bash
python3 -m venv venv
source venv/bin/activate
```

3. Установите зависимости:
```bash
pip install -r requirements.txt
```

4. Перейдите в директорию проекта с `manage.py` и выполните миграции:
```bash
cd yatube_api
python manage.py migrate
```

5. Запустите сервер разработки:
```bash
python manage.py runserver
```

6. Проверьте документацию API:
- Redoc: http://127.0.0.1:8000/redoc/

## Примеры запросов

### Получить JWT-токен
`POST /api/v1/jwt/create/`
```json
{
  "username": "test_user",
  "password": "test_password"
}
```

### Создать публикацию
`POST /api/v1/posts/`
```json
{
  "text": "Мой первый пост через API",
  "group": 1
}
```

### Получить комментарии к публикации
`GET /api/v1/posts/1/comments/`

### Подписаться на автора
`POST /api/v1/follow/`
```json
{
  "following": "author_username"
}
```

### Отфильтровать подписки
`GET /api/v1/follow/?search=author_username`

## Автор
Учебный проект Яндекс Практикума (доработка API Yatube).
