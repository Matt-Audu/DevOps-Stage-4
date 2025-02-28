# Use the official Golang image as the base image
FROM golang:1.21 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy the Go module files
COPY go.mod go.sum ./

# Download all dependencies
RUN go mod download

# Copy the rest of the application code
COPY . .

# Build the application
RUN CGO_ENABLED=0 GOOS=linux go build -o auth-api .

# Use a minimal Alpine-based image for the final stage
FROM alpine:latest

# Install necessary packages (e.g., ca-certificates for SSL)
RUN apk --no-cache add ca-certificates

# Set the working directory
WORKDIR /root/

# Copy the binary from the builder stage
COPY --from=builder /app/auth-api .

# Copy the .env file (if you have one)
COPY .env .

# Expose the port the application will run on
EXPOSE 8081

# Set environment variables (you can override these with `docker run -e`)

# Command to run the application
CMD ["./auth-api"]

