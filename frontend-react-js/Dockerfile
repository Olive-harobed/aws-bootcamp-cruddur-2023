# # Stage 1: Build the application
# FROM node:16.18 AS build

# ENV REACT_APP_BACKEND_URL=https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}
# WORKDIR /frontend-react-js
# COPY package*.json ./
# RUN npm install

# ENV PORT=3000
# EXPOSE ${PORT}

# COPY . .
# RUN npm run build

# # Stage 2: Create the production-ready image
# FROM nginx:alpine

# WORKDIR /usr/share/nginx/html

# RUN rm -rf ./*

# COPY --from=build /frontend-react-js/build .

# EXPOSE 80


FROM node:16.18

ENV PORT=3000

COPY . /frontend-react-js
WORKDIR /frontend-react-js
RUN npm install
EXPOSE ${PORT}
CMD ["./start.sh"]