# Step 1: Build the React app
FROM node:18 AS build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . ./
RUN npm run build

# Step 2: Serve the app using nginx
FROM nginx:alpine

# Copy the build folder to nginx's public directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 for nginx
EXPOSE 80

# Start nginx when the container runs
CMD ["nginx", "-g", "daemon off;"]
