FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm install

COPY . .
RUN npm run build

# Создаем директорию для статики
RUN mkdir -p /frontend_static

# Копируем собранные файлы в директорию для статики
RUN cp -r /app/build/* /frontend_static/

# Эта команда запустит встроенный сервер на Node.js, который будет раздавать
# содержимое директории /app/build на порте 8000
CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"]