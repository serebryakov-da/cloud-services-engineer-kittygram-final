FROM node:18-alpine

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci

COPY . .

CMD ["sh", "-c", "npm run build && cd /app/build && ln -sf static/js js && ln -sf static/css css && ln -sf static/media media"]
