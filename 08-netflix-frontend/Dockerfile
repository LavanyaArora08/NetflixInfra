# Use an official Node.js runtime as a base image (Node 14)
FROM node:14

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json (or npm-shrinkwrap.json) to the container
COPY package*.json ./

# Install a compatible version of npm
RUN npm install -g npm@6

# Install any needed packages specified in package.json, skipping optional ones
RUN npm install --no-optional

# Copy the rest of the application code to the container
COPY . .

# Build the project
RUN npm run build

# Define environment variable for NetflixMovieCatalog API service
ENV MOVIE_CATALOG_SERVICE=http://localhost:8080

# Make port 3000 available to the world outside this container
EXPOSE 3000

# Run the app when the container launches
CMD ["npm", "start"]
