# Stage 1
FROM node:10-alpine as build-step
# Create app directory
RUN mkdir -p /app
WORKDIR /app
# Install app dependencies
COPY ./package.json .
RUN npm install
# Build app
COPY . .
RUN npm run build --prod

# Stage 2
FROM nginx:1.17.1-alpine
COPY --from=build-step /app/dist /usr/share/nginx/html
