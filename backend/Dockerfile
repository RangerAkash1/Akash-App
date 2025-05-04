# Use official Node.js LTS image
FROM node:18-alpine

# Set working directory inside the container
WORKDIR /usr/src/app

# Copy only package files first to leverage Docker cache for dependencies
COPY package*.json ./

# Install production dependencies
RUN npm install --production

# Copy the rest of the backend source code to the container
COPY . .

# Expose Cloud Run's expected port
EXPOSE 8080

# Ensure it uses the dynamic port for Cloud Run
ENV PORT=8080
ENV NODE_ENV=production

# Start the backend app (update if entry file is not index.js)
CMD ["node", "server.js"]
