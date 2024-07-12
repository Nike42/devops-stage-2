# Use an official Node.js runtime as the base image for building the React app
FROM node:18-alpine AS build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application
RUN npm run build

# Use an official Nginx runtime as the base image for serving the built files
FROM nginx:alpine

# Copy build files from the build stage to Nginx public directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 to the Docker environment
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
