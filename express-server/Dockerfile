FROM node:10-alpine
# Create app directory
RUN mkdir -p /app
WORKDIR /app
# Install app dependencies
COPY ./express-server/package.json .
RUN npm install
# Bundle app source
COPY ./express-server .
EXPOSE 3000
CMD [ "node", "server.js" ]
