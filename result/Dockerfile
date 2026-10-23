FROM node:18-slim
WORKDIR /usr/local/app
COPY package*.json .
RUN npm install -j nodemon 
RUN npm ci && npm cache clean --force && mv /usr/local/app/node_modules /node_modules
COPY . .
EXPOSE 4000
CMD ["node","server.js"]