# saas-template

saas template

## Запуск шаблону SaaS

### 1. Створіть `.env` файл

У корені репозиторію створіть файл `.env` і заповніть його:

```env
# PostgreSQL
POSTGRES_USER=your_db_user
POSTGRES_PASSWORD=your_db_password
POSTGRES_DB=your_db_name
POSTGRES_PORT=5432

# Backend
BACKEND_PORT=8000

# Frontend
FRONTEND_PORT=3000

# Landing (Next.js)
LANDING_PORT=3001

# Test DB (опційно)
TEST_DB=your_test_db_name

## Запуск Docker контейнерів

У корені репозиторію виконайте:
docker-compose up -d --build

Список запущених контейнерів:
docker ps

Логи backend:
docker logs saas-template_backend_1

Логи frontend:
docker logs saas-template_frontend_1

Логи landing:
docker logs saas-template_landing_1

Доступ до сервісів
Backend API: http://localhost:${BACKEND_PORT}
Frontend: http://localhost:${FRONTEND_PORT}
Landing: http://localhost:${LANDING_PORT}

Щоб зупинити та видалити контейнери та volumes:
docker-compose down -v

Mobile Development (React Native / Expo)
npm install -g expo-cli
Запуск проекту
cd mobile
expo start


```
