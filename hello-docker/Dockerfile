FROM node:19-alpine

COPY package.json /app/
COPY package-lock.json /app/
COPY src /app/
COPY .gitignore /app/

WORKDIR /app

RUN npm install

CMD ["node", "server.js"]