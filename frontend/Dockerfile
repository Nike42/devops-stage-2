# Dockerfile for React frontend
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

FROM nginx:alpine
# Copy build files to Nginx public directory
COPY --from=build /app/build /usr/share/nginx/html
# Expose port 80 to the Docker environment
EXPOSE 80
# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
