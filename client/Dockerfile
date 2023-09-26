# Use a base image with Node.js pre-installed
FROM node:14-alpine

# Add the following lines
ENV CI=true
ENV WDS_SOCKET_PORT=0

# Set the working directory in the container
WORKDIR /usr/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Clear the npm cache
RUN npm cache clean --force

# Install some dependencies
RUN npm install

# Copy the rest of your application code
COPY ./ ./

# Default command
CMD ["npm", "start"]



# FROM node:alpine



# WORKDIR /app
# COPY package.json ./
# RUN npm install
# COPY ./ ./

# CMD ["npm", "start"]