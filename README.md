## Проект Django: Система управления курсами

Этот проект представляет собой веб-приложение на Django, которое позволяет пользователям просматривать и проходить курсы, оставлять комментарии. Он включает в себя функциональность для управления курсами, темами и уроками, а также систему аутентификации пользователей.

Этот README предоставляет общее представление о проекте и его функциональности.
Запущенный сайт доступен по адресу [ссылка](http://vaibron.beget.tech)

### Оглавление

1. [Установка](#установка)
2. [Использование](#использование)
3. [Модели](#модели)
4. [URLs](#urls)

---

## Установка

Для запуска проекта вам потребуется установить Python и Django. Следуйте инструкциям ниже:

1. **Клонируйте репозиторий:**

   ```bash
   git clone https://github.com/Vaibron/L-platform-MySql-.git
   cd L-platform-MySql-
   ```

2. **Создайте виртуальное окружение:**

   ```bash
   python -m venv venv
   source venv/bin/activate  # Для macOS/Linux
   venv\Scripts\activate  # Для Windows
   ```

3. **Установите зависимости:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Настройте базу данных:**

   Убедитесь, что у вас установлен MySQL и создана база данных. Настройте параметры подключения в `base/settings.py`.

5. **Примените миграции:**

   ```bash
   python manage.py migrate
   ```

6. **Создайте суперпользователя:**

   ```bash
   python manage.py createsuperuser
   ```

7. **Запустите сервер:**

   ```bash
   python manage.py runserver
   ```

Теперь вы можете открыть браузер и перейти по адресу `http://127.0.0.1:8000/`, чтобы увидеть приложение.

---

## Использование

После запуска сервера вы можете:

- **Просматривать курсы**: На главной странице отображаются все доступные курсы.
- **Регистрация и вход**: Пользователи могут зарегистрироваться и войти в систему.
- **Проходить курсы**: После выбора курса пользователи могут просматривать темы и уроки.
- **Оставлять комментарии**: Пользователи могут оставлять комментарии к курсам.

---

## Модели

### Course

Модель `Course` представляет курс и содержит следующие поля:

- `title`: Название курса.
- `description`: Описание курса.
- `created_at`: Дата создания курса.
- `updated_at`: Дата последнего обновления.
- `image`: Изображение курса.
- `duration`: Длительность курса.
- `difficulty_level`: Уровень сложности курса.
- `is_available`: Доступность курса.
- `allow_comments`: Разрешение на комментарии.

### Topic

Модель `Topic` представляет тему в рамках курса и имеет поля:

- `course`: Связь с моделью `Course`.
- `title`: Название темы.
- `order`: Порядок темы в курсе.

### Lesson

Модель `Lesson` представляет урок и содержит:

- `topic`: Связь с моделью `Topic`.
- `title`: Название урока.
- `content`: Содержимое урока.
- `video_code`: Код для встраивания видео.
- `order`: Порядок урока в теме.

### Comment

Модель `Comment` позволяет пользователям оставлять комментарии к курсам и содержит:

- `user`: Связь с моделью `User `.
- `course`: Связь с моделью `Course`.
- `text`: Текст комментария.
- `created_at`: Дата создания комментария.

---

## URLs

Основные маршруты приложения:

- `/courses/`: Главная страница с курсами.
- `/courses/<int:course_id>/`: Страница конкретного курса.
- `/courses/start/<int:course_id>/`: Начало прохождения курса.
- `/courses/lesson/<int:lesson_id>/`: Страница конкретного урока.
- `/accounts/login/`: Страница входа.
- `/accounts/register/`: Страница регистрации.

---
