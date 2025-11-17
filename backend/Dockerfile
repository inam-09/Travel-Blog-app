# Base image for backend
FROM node:24-alpine 

# Author Name Its Optional 
LABEL maintainer="Professor khan <professork900@gmail.com>"
LABEL author="Professor Khan"
LABEL organization="DevOps" 

# Create a non-root user & Set Permissions 
RUN useradd -m appuser && chown -R appuser:appuser /app
USER appuser

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./
RUN npm ci --only=production --no-audit --no-fund


# Copy the rest of the application code to the working directory
COPY . .

RUN npm run test

COPY .env.sample .env
# Expose the port the app runs on
EXPOSE 5000

# Command to start the backend server
CMD ["npm", "start"]
