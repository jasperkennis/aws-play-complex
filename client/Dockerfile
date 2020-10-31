# BUILD
# FROM node:alpine as builder
FROM node:alpine
WORKDIR '/app'

COPY package.json .
RUN npm install

COPY . .

RUN npm run build

# RUN SERVER
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etch/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html
