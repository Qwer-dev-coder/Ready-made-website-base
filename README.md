# ScLab — Code Laboratory

Сайт лаборатории кодов, скриптов, ботов и инструментов разработки в стиле Lolzteam.
Поддерживает локальный запуск на Python 3 (`backend/local/server.py` + SQLite), а также облачное развёртывание на Firebase.

## Структура

- `public/` — страницы, стили, изображения и браузерные скрипты ScLab;
- `scripts/init_sclab_db.py` — быстрая инициализация и сброс базы данных SQLite;
- `backend/local/` — локальный Python-сервер для работы без Firebase;
- `data/` — локальная SQLite-база, не публикуется и исключена из Git;
- `functions/` — облачный API для входа, профиля, админки и ключей;
- `docs/` — актуальная инструкция по Firebase;
- `tests/` — проверки и тесты API и статических файлов.

## Локальный запуск

Запустите `start.bat`. Нужен Python 3. Сайт откроется по адресу `http://localhost:8080`.

- Логин администратора: `admin`
- Пароль администратора: `admin123`
- Админ-панель: `http://localhost:8080/admin/`
- Личный кабинет: `http://localhost:8080/profile/`

## Проверки

```powershell
npm install --prefix functions
npm run check
```

Полный запуск эмуляторов:

```powershell
firebase emulators:start --only hosting,functions,firestore --project demo-sclab
```

Для теста первого администратора создайте временный файл `functions/.secret.local`:

```text
INITIAL_ADMIN_TOKEN=любая-длинная-тестовая-строка
```

Этот файл уже исключён из Git. Для публикации используйте Secret Manager через Firebase CLI, а не локальный файл.

## Публикация

Полная пошаговая инструкция: [docs/FIREBASE_DEPLOYMENT.md](docs/FIREBASE_DEPLOYMENT.md).

Короткая команда после подключения проекта и создания секрета:

```powershell
firebase deploy --only hosting,functions,firestore
```

Платёжный провайдер и ссылка на загрузку клиента намеренно не включены: их нужно подключить отдельно после получения рабочих реквизитов и файла продукта.
