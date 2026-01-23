# Стадия сборки
FROM node:18-alpine AS build
WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci

COPY . .
RUN npm run build

# Финальный образ — только статические файлы
FROM nginx:1.25-alpine
COPY --from=build /app/build /static