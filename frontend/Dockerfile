# === Build stage ===
FROM node:20-alpine AS build

# Робоча директорія
WORKDIR /app

# Копіюємо package файли та встановлюємо залежності
COPY package.json package-lock.json ./
RUN npm ci

# Копіюємо весь код і збираємо фронтенд
COPY . .
RUN npm run build

# === Production stage ===
FROM nginx:stable-alpine

# Копіюємо зібраний фронтенд у nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Копіюємо конфіг nginx (опційно)
# COPY infra/nginx/frontend.conf /etc/nginx/conf.d/default.conf

# Проброс порту
EXPOSE 3000

# Запуск nginx
CMD ["nginx", "-g", "daemon off;"]
