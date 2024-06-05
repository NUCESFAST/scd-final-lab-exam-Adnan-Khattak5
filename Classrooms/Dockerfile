# Classrooms Dockerfile
FROM node:14

WORKDIR /1141_backend

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3141
CMD ["npm", "start"]
