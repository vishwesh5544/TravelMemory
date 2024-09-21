# Stage 1: Build the React app
FROM node:18-alpine AS builder

# Set the working directory
WORKDIR /app

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install the dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application
RUN npm run build

# Stage 2: Serve the React app with Nginx
FROM nginx:alpine

# Copy the built React app from the builder stage to Nginx's default public directory
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80 for the Nginx server
EXPOSE 80

# Start Nginx when the container launches
CMD ["nginx", "-g", "daemon off;"]


# # Use an official Node.js runtime as a parent image
# FROM node:18-alpine

# # Set the working directory
# WORKDIR /app

# # Copy the package.json and package-lock.json files
# COPY package*.json ./

# # Install the dependencies
# RUN npm install

# # Copy the rest of the application code
# COPY . .

# # Build the React application
# RUN npm run build

# # Install `serve` to serve the built application
# RUN npm install -g serve

# # Set the environment variable to indicate production
# ENV NODE_ENV=production

# # Expose port 3000 to the outside world
# EXPOSE 3000

# # Start the application
# CMD ["serve", "-s", "build", "-l", "3000"]
