# Base image
FROM node:15.4 as build
WORKDIR /app
RUN npm install -g @quasar/cli
COPY package*.json ./
COPY . ./
RUN npm install && quasar build
CMD ["sh", "-c", "tail -f /dev/null"]
