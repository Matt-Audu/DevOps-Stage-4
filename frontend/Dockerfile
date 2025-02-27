FROM node:14-alpine AS builder

WORKDIR /app

# Copy package.json and package-lock.json first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code, including the .env file and server.js
COPY . . 

# Build the application
RUN npm run build

# Expose application port
EXPOSE 8080

# Run the application
CMD ["npm", "start"]