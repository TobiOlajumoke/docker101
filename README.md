## What is Docker?
Docker is a tool that allows you to create and manage lightweight, portable containers that can run your applications in any environment, without worrying about dependencies or other environmental factors.

## Docker Basics
### Dockerfile
A Dockerfile is a text file that contains instructions for building a Docker image. It contains a series of commands that are executed one after the other to create an image. Here's an example of a simple Dockerfile:

```
FROM python:3.9

WORKDIR /app

COPY . /app

RUN pip install --no-cache-dir -r requirements.txt

CMD [ "python", "app.py" ]
```
In this Dockerfile, we're using the official Python 3.9 image as the base image, setting the working directory to /app, copying the contents of the current directory into the container, installing the dependencies specified in requirements.txt, and setting the default command to run the app.py file.

### Docker Image
A Docker image is a snapshot of an application and its dependencies. It's created by running the commands in a Dockerfile. You can think of an image as a blueprint for creating containers.

To build an image, you run the docker build command, specifying the path to the directory that contains the Dockerfile. For example:

```
docker build -t my-app .
```
This command will build an image named my-app from the Dockerfile in the current directory (.).

### Docker Container
A Docker container is a running instance of an image. You can think of a container as a lightweight, isolated virtual environment. Containers have their own file system, networking, and processes, but they share the kernel of the host operating system.

To run a container, you run the docker run command, specifying the name of the image to run. For example:

```
docker run my-app
```
This command will run a container from the my-app image.

### Docker Compose
Docker Compose is a tool that allows you to define and run multi-container Docker applications. You can use it to define the services that make up your application, specify their dependencies and configuration, and run them all with a single command.

Here's an example of a docker-compose.yml file that defines a simple two-service application:

```
version: "3.9"

services:
  web:
    build: .
    ports:
      - "8000:8000"
  db:
    image: postgres
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
```
In this docker-compose.yml file, we're defining two services: web and db. The web service is built from the current directory (.), and its container will be accessible on port 8000. The db service is created from the official postgres image, and we're setting the POSTGRES_USER and POSTGRES_PASSWORD environment variables.

To start the application, we can run:

```
docker-compose up
```
This command will start both the web and db services and connect them together.

Sample Use Cases
Running a Python Application
Let's say you have a Python application that depends on certain Python packages. You can create a Dockerfile to build an image of your application and its dependencies, and then run a container from that image.

Here's an example of a simple Python Flask application that uses Docker:

```
# Dockerfile

FROM python:3.9

WORKDIR /app

COPY . /app

RUN pip install --no-cache-dir -
```