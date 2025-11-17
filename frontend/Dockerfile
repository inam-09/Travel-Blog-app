# Use official Node image
FROM node:24-alpine

# Author Name Its Optional 
LABEL maintainer="Professor khan <professork900@gmail.com>"
LABEL author="Professor Khan"
LABEL organization="DevOps" 

# Set Working Dir
WORKDIR /frontend

# Create a non-root user & Set Permissions 
RUN useradd -m appuser && chown -R appuser:appuser /app
USER appuser

# Install dependencies
COPY package*.json ./
RUN npm ci --only=production --no-audit --no-fund

# Copy source and build
COPY . .

# Copy ENV file
COPY .env.sample .env.local

# Expose Port 
EXPOSE 3000

# Default command
CMD ["npm","run","dev", "--","--host"]
