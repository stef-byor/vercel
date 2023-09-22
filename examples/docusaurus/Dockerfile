# Use the official Node.js image as the base image
FROM node:18-alpine as builder

# Set the working directory in the container
WORKDIR /app

# Install build tools
RUN apk add --update --no-cache autoconf automake libtool gifsicle pngquant build-base libpng-dev nasm

# Copy package.json and package-lock.json to the working directory
COPY . .

# Install project dependencies
RUN yarn

# Copy the entire project directory to the working directory
COPY . .

# Build the Docusaurus website (replace 'npm run build' with your build script if different)
RUN npm run build

RUN chown -R 10500:10500 "/app"

USER 10500

# Expose the port that Docusaurus will run on (usually 3000)
EXPOSE 3001

# Start Docusaurus (replace 'npm start' with your start script if different)
CMD ["npm", "start"]
