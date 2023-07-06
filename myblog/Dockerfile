FROM node:20-alpine3.17

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . .

EXPOSE 3000
# required for docker desktop port mapping. React app run on port 3000 by default

CMD ["npm", "start"]