# Client Dockerfile
FROM node:14

WORKDIR /1141_frontend

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 1141
CMD ["npm", "start"]
