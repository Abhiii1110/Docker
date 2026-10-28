# Docker
To get started with Docker, you need two things: a Dockerfile (the blueprint recipe that packages your app) and Docker CLI commands (to build and run that recipe).
Here is the essential code and setup for a basic project.

1. The Blueprint: Dockerfile

Create a file named exactly Dockerfile (no file extension) in your project root folder.
dockerfile
# 1. Choose a starting template (Base Image)
FROM node:18-alpine

# 2. Create a folder inside the container for your app code
WORKDIR /app

# 3. Copy your project configuration and install dependencies
COPY package*.json ./
RUN npm install

# 4. Copy the rest of your application code into the container
COPY . .

# 5. Expose the port your application listens on internally
EXPOSE 3000

# 6. The default command to run when the container starts up
CMD ["npm", "start"]
