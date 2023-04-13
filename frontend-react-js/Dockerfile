# Stage 1: Build the application
FROM node:16.18 AS build


WORKDIR /frontend-react-js
COPY package*.json ./
RUN npm install

ENV PORT=3000
EXPOSE ${PORT}

COPY . .
RUN npm run build

# Stage 2: Create the production-ready image
FROM nginx:alpine

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=build /frontend-react-js/build .

EXPOSE 80


