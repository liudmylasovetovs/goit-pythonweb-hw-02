## Завдання

1. Використовуючи команду git clone, клонуйте репозиторій за адресою <https://github.com/GoIT-Python-Web/FullStack-Web-Development-hw2>. Перейдіть у клонований каталог.

2. Створіть Dockerfile із вказівками для створення образу Docker застосунку.

3. Напишіть docker-compose.yaml з конфігурацією для застосунку та PostgreSQL.

4. Використайте Docker Compose для побудови середовища, команду docker-compose up для запуску середовища.

## Розв'язання

1. Клонуємо репозиторій: git clone <https://github.com/GoIT-Python-Web/FullStack-Web-Development-hw2>

2. Створюємо Dockerfile із вказівками для створення образу Docker застосунку

     Встановлення бібліотек і запуск:

        RUN pip install -r requirements.txt

        ENTRYPOINT ["python", "main.py"]

3. Створюємо docker-compose.yaml з конфігурацією для застосунку та PostgreSQL:

4. Побудова і запуск контейнера

    - виправляємо помилку із встановленням psycopg2 на Linux, додамо умови platform_system в requirements.txt:

        psycopg2==2.9.9 ; python_version >= "3.10" and python_version < "4.0" and platform_system == "Windows"
        psycopg2-binary==2.9.9 ; python_version >= "3.10" and python_version < "4.0" and platform_system == "Linux"

    - Запускаємо контейнер docker compose up --build -d

    - вказуємо правильний хост в conf/db.py
  
        SQLALCHEMY_DATABASE_URL = f"postgresql+psycopg2://postgres:567234@postgres:5432/hw02"

    - Перевіримо роботу застосунку, відкриваємо в браузері порт, який налаштували:
  
        \img\localhossceen.png
