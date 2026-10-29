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

To run your very first Docker program, you can use the official pre-built validation image.
Open your terminal or command prompt and run the following command:
bash
docker run hello-world
Use code with caution.

What Happens Behind the Scenes

When you execute this command, Docker executes the following steps:
1. Checks local cache: The Docker client looks for the hello-world image on your computer.
2. Pulls from Docker Hub: Because it is your first time, the image won't be found locally. Docker automatically connects to Docker Hub and downloads it.
3. Creates the container: The Docker engine spins up a isolated container container instance from that image.
4. Executes the code: The container runs a small script that prints a "Hello from Docker!" confirmation message right into your terminal before immediately closing.

Writing Your Own First Custom Docker Program

If you want to build and run a program that you wrote yourself, follow this simple Python example:

1. Create a Project File

Create a new folder on your computer and place a file inside named app.py containing this single line of code:
python
print("Hello! This is my first custom Docker application.")
Use code with caution.

2. Create the Dockerfile

In the exact same folder, create a file named Dockerfile (with no file extension). Paste the following configuration into it:
dockerfile
# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Copy the current directory contents into the container
COPY app.py /app.py

# Run app.py when the container launches
CMD ["python", "/app.py"]
Use code with caution.

3. Build the Image

Open your terminal in that project folder and build your custom image by running:
bash
docker build -t my-first-docker-app .
Use code with caution.
(Don't forget the period . at the very end, which tells Docker to look in the current folder.)

4. Run Your Program

Once built successfully, launch your container using:
bash
docker run my-first-docker-app
