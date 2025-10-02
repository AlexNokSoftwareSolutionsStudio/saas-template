# === Build stage ===
FROM node:20-alpine AS build

WORKDIR /app

# Копіюємо package файли та встановлюємо залежності
COPY package.json package-lock.json ./
RUN npm ci

# Копіюємо весь код і будуємо проект
COPY . .
RUN npm run build

# === Production stage ===
FROM nginx:stable-alpine

# Копіюємо зібраний фронтенд у nginx
COPY --from=build /app/.next /usr/share/nginx/html
COPY --from=build /app/public /usr/share/nginx/html

# (опційно) власний конфіг nginx
# COPY infra/nginx/landing.conf /etc/nginx/conf.d/default.conf

EXPOSE 3001

CMD ["nginx", "-g", "daemon off;"]
