# Stage 1: Build the React app using Node.js and Ubuntu base image
FROM node:18 AS builder

# Set the working directory in the builder container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the entire project directory to the working directory
COPY . .

# Build the React app (replace 'npm run build' with your build script if different)
RUN npm run build

# Stage 2: Create the final Alpine-based image
FROM nginx:alpine

# Copy the built React app from the builder stage to the nginx web server's HTML directory
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80 (default for HTTP traffic)
EXPOSE 80

# Start the nginx web server when the container is run
CMD ["nginx", "-g", "daemon off;"]
