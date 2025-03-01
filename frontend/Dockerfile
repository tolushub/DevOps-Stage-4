# frontend/Dockerfile
# Use a Node.js image to build the Vue.js application
FROM node:14 AS build-stage
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Use a lightweight Node.js image for serving the static files
FROM node:16-alpine AS runtime-stage
WORKDIR /app

# Copy the built artifacts from the build stage
COPY --from=build-stage /app/dist /app/dist

# Install the 'serve' package globally
RUN npm install -g serve

# Expose port 80 for serving the application
EXPOSE 80

# Serve the static files using 'serve'
CMD ["serve", "-s", "/app/dist", "-l", "80"]
