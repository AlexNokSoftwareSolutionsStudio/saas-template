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

# Test DB (опційно)
TEST_DB=your_test_db_name
```
