# AAT_01_PHP
Альтернативная аттестационная работа 01. Разработка веб-приложения для создания и прохождения тестов

# 🧮 Test Application (Math Tests)

Веб-приложение для создания и прохождения математических тестов с расширенной аналитикой результатов.

## 🌟 Особенности
- **Без зависимостей**: Не требует Composer или сторонних пакетных менеджеров
- **Простая установка**: Все компоненты включены в репозиторий
- **Полная портативность**: Работает на любом PHP-хостинге
- **Безопасность**: Валидация данных + CSRF-защита

## 📂 Структура проекта
```bash
project/
├── app/                  # Ядро приложения
│   ├── Controllers/      # Контроллеры
│   │   ├── ResultController.php  # Логика результатов
│   │   └── TestController.php    # Управление тестами
│   ├── Models/           # Модели данных
│   │   ├── Result.php    # Работа с результатами
│   │   └── Test.php      # Загрузка тестов
│   ├── Views/            # Шаблоны страниц
│   │   ├── dashboard.php # Админ-панель
│   │   ├── home.php      # Главная страница
│   │   ├── result.php    # Страница результатов
│   │   └── test.php      # Страница теста
│   ├── bootstrap.php     # Инициализация приложения
│   └── Libraries/
│       └── FPDF/         # Встроенная библиотека FPDF
│           ├── font/     # Шрифты
│           ├── fpdf.php  # Основной класс
│           └── ...       # Доп. файлы библиотеки
├── config/               # Конфигурация
│   └── env.php           # Настройки окружения
├── data/                 # Хранение данных
│   ├── tests/            # Каталог тестов
│   │   └── math.json     # Пример теста
│   └── results.json      # База результатов
├── public/               # Публичная директория
│   ├── assets/           # Ресурсы
│   │   └── css/
│   │       └── style.css # Кастомные стили
│   ├── .htaccess         # Настройки Apache
│   └── index.php         # Точка входа

```

🚀 Запуск приложения
Требования
PHP 7.4+ (с поддержкой сессий и JSON)

Права на запись в папку data/

Установка (3 шага)
Скачайте и распакуйте архив:

```bash
wget https://github.com/zabudico/math-test/archive/main.zip
unzip main.zip -d /var/www/html
```

Настройте права:

```bash
chmod -R 755 /var/www/html/project/data
```

Запустите встроенный сервер:

```bash
cd /var/www/html/project
php -S localhost:8000 -t public
```

Откройте в браузере:
http://localhost:8000


🧪 Формат тестов
data/tests/math.json:

```json
{
  "title": "Основы математики",
  "questions": [
    {
      "text": "Сколько будет 2 + 2?",
      "type": "radio",
      "options": ["3", "4", "5"],
      "correct": [1]
    },
    {
      "text": "Выберите простые числа",
      "type": "checkbox",
      "options": ["2", "4", "7"],
      "correct": [0, 2]
    }
  ]
}
```

📊 Хранение данных
Результаты (data/results.json)

```json
[
  {
    "username": "Иван",
    "score": 4,
    "percent": 80.0,
    "date": "2023-10-25 14:45:00"
  }
]
```

### Схема данных
Поле	    Тип	      Описание
username	string	  Имя пользователя
score	    integer	  Количество баллов
percent	  float	    Процент правильных ответов
date	    datetime	Дата прохождения теста

🖼️ Интерфейс приложения

Главная страница

![image](https://github.com/user-attachments/assets/01960fde-9cc1-430b-a0d0-2bc38705f8b1)

Стартовая страница с кнопкой начала теста

Прохождение теста

![image](https://github.com/user-attachments/assets/4efa8e63-cd4a-426f-84b0-cf802cce303c)

![image](https://github.com/user-attachments/assets/4b0a8679-b1fc-4a65-b3ac-20e5887f7dc1)


Результаты

![image](https://github.com/user-attachments/assets/1ea2684a-e0f5-4dda-83b2-92860c83598b)


Таблица с историей всех попыток

![image](https://github.com/user-attachments/assets/5ae915e2-61ae-4b6f-8bd9-bb6879011b34)

PDF-отчёт

![image](https://github.com/user-attachments/assets/ce4e0459-f455-472b-b52f-e4ce2554e8ba)

Пример экспортированного отчёта

🔧 Технические детали

Используемые технологии

Компонент	  Версия	Назначение
PHP	        8.0+	  Бэкенд-логика
FPDF	      1.84	  Генерация PDF-документов
JSON	      -	       Хранение данных

Безопасность

- CSRF-токены для всех форм
- Экранирование вывода (htmlspecialchars)
- Валидация типов ответов
- Защита путей через .htaccess
 
