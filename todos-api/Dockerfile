FROM node:8-alpine AS builder

WORKDIR /app

# Copy package.json and package-lock.json first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code, including the .env file and server.js
COPY . .

# Expose application port
EXPOSE 8082

# Run the application
CMD ["npm", "start"]