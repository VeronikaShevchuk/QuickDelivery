# Используем базовый образ Python
FROM python:3.8-slim

# Устанавливаем рабочую директорию
WORKDIR /app

# Копируем файлы приложения в контейнер
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . /app

# Устанавливаем зависимости
RUN pip install --no-cache-dir -r requirements.txt
RUN apt-get update && \
    apt-get install -y postgresql-client && \
    rm -rf /var/lib/apt/lists/*

# Определяем команду для запуска приложения
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
