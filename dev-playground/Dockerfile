# Use Node.js 18 LTS as base image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy package.json files
COPY package.json ./
COPY babel.config.json ./
COPY dev-playground/package.json ./dev-playground/

# Install ALL dependencies (including dev) for build
RUN npm install

# Copy source files needed for build
COPY src/ ./src/

# Build the project (compile src to js)
RUN npm run build:node

# Install dev-playground dependencies
RUN cd dev-playground && npm install --production

# Copy remaining files
COPY examples/fonts/ ./examples/fonts/
COPY dev-playground/ ./dev-playground/

# Expose the port
EXPOSE 1234

# Set working directory to dev-playground
WORKDIR /app/dev-playground

# Start the server
CMD ["node", "server.js"]
