# todos-api/Dockerfile
FROM node:14
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
ENV REDIS_HOST=redis-queue
ENV REDIS_PORT=6379
ENV JWT_SECRET=myfancysecret
EXPOSE 8082
CMD ["npm", "start"]