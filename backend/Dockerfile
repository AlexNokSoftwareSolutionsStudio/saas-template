# === Базовий образ ===
FROM python:3.11-slim

# === Робоча директорія ===
WORKDIR /app

# === Копіюємо Poetry файли та встановлюємо залежності ===
COPY pyproject.toml poetry.lock ./
RUN pip install --upgrade pip \
    && pip install poetry \
    && poetry config virtualenvs.create false \
    && poetry install --no-root --no-interaction --no-ansi

# === Копіюємо решту коду ===
COPY . .

# === Додаємо wait-for-it ===
COPY wait-for-it.sh /wait-for-it.sh
RUN chmod +x /wait-for-it.sh

# === EXPOSE порт (можна через змінну з docker-compose) ===
EXPOSE 8000

# === Запуск з чеканням бази ===
CMD ["/wait-for-it.sh", "db:5432", "--timeout=30", "--strict", "--", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
