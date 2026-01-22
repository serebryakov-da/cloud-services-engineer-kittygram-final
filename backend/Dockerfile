# Используем официальный образ Python 3.9
FROM python:3.9-slim

# Устанавливаем системные зависимости (если нужны для psycopg2 - PostgreSQL драйвер)
RUN apt-get update && apt-get install -y \
    gcc \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

# Создаем рабочую директорию
WORKDIR /app

# Копируем зависимости
COPY requirements.txt .

# Обновляем pip и устанавливаем зависимости
RUN pip install --upgrade pip && \
    pip install -r requirements.txt --no-cache-dir

# Копируем весь проект
COPY . .

# Запускаем Gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]
