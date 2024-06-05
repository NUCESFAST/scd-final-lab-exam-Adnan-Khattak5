# Use the official Node.js image as the base image
FROM node:14

# Set the working directory to /3141
WORKDIR /3141_backend

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Expose the application on port 3141
EXPOSE 3141

# Start the application
CMD ["node", "index.js"]
