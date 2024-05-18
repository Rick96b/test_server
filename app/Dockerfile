        
# dev

# устанавливаем официальный образ Node.js
FROM node:16.10.0-alpine AS dev

# указываем рабочую (корневую) директорию
WORKDIR /app

# копируем основные файлы приложения в рабочую директорию
COPY package.json package-lock.json ./

# устанавливаем указанные зависимости NPM на этапе установки образа
RUN npm install

# после установки копируем все файлы проекта в корневую директорию
COPY . ./

# запускаем основной скрипт в момент запуска контейнера
CMD npm start

# production
FROM node:16.10.0-alpine AS production
RUN apk add --no-cache tzdata
ENV TZ Europe/Moscow
ENV NODE_PATH /opt/server/node_modules

WORKDIR /opt/server/

COPY /*.json ./
RUN npm i

CMD ["sh", "-c", "npm run start"]

    