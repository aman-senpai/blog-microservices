# Use a base image with Node.js pre-installed
FROM node:24-alpine

# Set the working directory in the container
WORKDIR /usr/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of your application code
COPY ./ ./

# Default command (Vite dev server, bound to 0.0.0.0 via vite.config.js)
CMD ["npm", "run", "dev"]
