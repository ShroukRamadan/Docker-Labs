FROM node:16-alpine As builder

# Set the working directory to /app inside the container
WORKDIR /app

COPY package*.json ./

# Copy app files
COPY . .

# Install dependencies (npm ci makes sure the exact versions in the lockfile gets installed)
RUN npm ci

# Build the app
RUN npm run build


# Bundle static assets with nginx
FROM nginx:1.21.0-alpine 

# Copy built assets from `builder` image
COPY --from=builder /app/build /usr/share/nginx/html


# Expose port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]


