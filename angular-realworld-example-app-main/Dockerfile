# Step 1: Build the Angular app
FROM node:20 AS build

WORKDIR /app

COPY package*.json ./

# Skip husky install during build
ENV HUSKY_SKIP_INSTALL=true

RUN npm install

COPY . .

RUN npm run build --prod

# Step 2: Serve the app using an Nginx server
FROM nginx:alpine

COPY --from=build /app/dist/angular-realworld /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

