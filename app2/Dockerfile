# Base image
FROM node:15.4 as build
WORKDIR /app
RUN npm install -g @quasar/cli
COPY package*.json ./
COPY . ./
RUN npm install && quasar build

FROM nginx:1.19
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist /usr/share/nginx/html/
EXPOSE 80