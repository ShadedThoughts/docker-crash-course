FROM node:20-alpine3.17

RUN npm install -g nodemon

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 4000
# required for docker desktop port mapping

CMD ["npm", "run", "dev"]