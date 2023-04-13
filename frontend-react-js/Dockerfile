# FROM node:16.18

# ENV PORT=3000

# COPY . /frontend-react-js
# WORKDIR /frontend-react-js
# RUN npm install
# EXPOSE ${PORT}
# CMD ["./start.sh"]

# Stage 1: Build the application
FROM node:16.18 AS build

WORKDIR /frontend-react-js
COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: Create the production-ready image
FROM node:16.18-alpine

ENV PORT=3000

WORKDIR /frontend-react-js
COPY --from=build /frontend-react-js/build ./build
COPY --from=build /frontend-react-js/start.sh .

RUN apk update && apk add --no-cache bash
RUN chmod +x ./start.sh

EXPOSE ${PORT}

CMD ["./start.sh"]
