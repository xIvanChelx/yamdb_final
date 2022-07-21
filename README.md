# YAMDB_FINAL
![example workflow](https://github.com/xIvanChelx/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

REST API проект для сервиса YaMDb — сбор отзывов о фильмах, книгах или музыке.
Проект доступен по адресу http://ivanchel.servebeer.com

## Документация API YaMDb
Документация доступна по эндпойнту: http://ivanchel.servebeer.com/redoc/

## Описание

Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles).
Произведения делятся на категории: (Categories).
Произведению также может быть присвоен жанр (Genre).
Сами произведения не хранятся в YaMDB.
Пользователи оставляют к произведениям текстовые отзывы (Review)
и ставят произведению оценку в диапазоне от одного до десяти (целое число);
из пользовательских оценок формируется усреднённая оценка произведения —
рейтинг (целое число).
На одно произведение пользователь может оставить только один отзыв.

У проекта есть backend, API, нет frontend.

### Как запустить проект:

Клонируем репозиторий и переходим в него:
```bash
git clone https://github.com/xIvanChelx/yamdb_final.git
cd yamdb_final
```

Создаем и активируем виртуальное окружение:
```bash
python -m venv venv
source /venv/Scripts/activate
```

Ставим зависимости из requirements.txt:
```bash
cd api_yamdb
pip install -r requirements.txt
```

Переходим в папку с файлом docker-compose.yaml:
```bash
cd ..
cd infra
```

Поднимаем контейнеры:
```bash
docker-compose up -d --build
```

Выполняем миграции:
```bash
docker-compose exec web python manage.py migrate
```

Создаем суперпользователя:
```bash
docker-compose exec web python manage.py createsuperuser
```

Собираем статику:
```bash
docker-compose exec web python manage.py collectstatic --no-input
```