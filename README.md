# Docker

### Learning

## What is docker?

- Docker is a virtualization Software.
- It makes Developing and Deploying applications much easier.
- Packages application with all the necessary dependencies, configuration, system tools and runtime.
  -- A standard unit that has everything the application needs to run. They are all packaged into a container.

### What problems that docker help solve?

```sh
Docker is a tool that helps to solve the problem of software dependencies. When you install software on your computer, you often have to install a lot of other software that the software depends on. This can be a pain, especially if you're not sure what all the dependencies are. Docker solves this problem by creating a "container" that contains all of the software that a particular piece of software needs. This way, you can just install the software in the container and it will work without having to worry about dependencies.
```

## Developer process before containers?

```sh
- Before containers, developers had to manually install and configure all of the software dependencies for their applications. This was a time-consuming and error-prone process. If a developer made a mistake, it could take hours or even days to fix.

- Containers made it much easier to develop applications. With containers, developers could simply create a container image that contained all of the software dependencies for their application. Then, they could run their application in a container on any machine that had Docker installed.

- This made it much easier to develop and deploy applications. Developers could now focus on writing code, and they didn't have to worry about installing and configuring software. Containers also made it easier to share applications with other developers.
```

## Development process with containers?

- Own isolated environment.
- Postgres packaged with all dependencies. (docker run progress)

- Same Commands (docker run ...)

- Standardizes process of running any service on any local dev environment.

```sh
- The development process with containers is much simpler than the development process without containers. With containers, developers can simply create a container image that contains all of the software dependencies for their application. Then, they can run their application in a container on any machine that has Docker installed.

- This makes it much easier to develop and deploy applications. Developers can now focus on writing code, and they don't have to worry about installing and configuring software. Containers also make it easier to share applications with other developers.
```

## Deployment process before containers

- The developer could create an artifact of a zip file and the installation instructions handed over to Ops team
- Ops team handles installing and configuring apps and its dependencies.

```sh
- Before containers, the deployment process was much more complicated. In order to deploy an application, you would need to manually install all of the necessary software on the target machine. You would also need to configure the application to work on that machine. This could be a very time-consuming and error-prone process.

- With containers, the deployment process is much simpler. You can simply create a container image that contains all of the necessary software for your application. Then, you can deploy the container to any machine that has Docker installed. The container will automatically install and configure itself on the target machine. This makes the deployment process much faster and more reliable.
```

## Deployment process with Docker

```sh
- The deployment process with Docker is very simple. First, you need to create a Dockerfile. A Dockerfile is a text file that describes how to build a Docker image. Once you have created a Dockerfile, you can build the image using the docker build command. Once the image is built, you can deploy it to a target machine using the docker run command. The docker run command will start a new container from the specified image.
```

## Docker vs Virtual Machines?

```sh
- Containers and virtual machines are two different ways to package and run software. Containers are lightweight and share the kernel of the host machine with other containers. Virtual machines, on the other hand, are more resource-intensive and require a full copy of the operating system.

- Containers are useful for developing and deploying applications quickly. They allow developers to quickly create and test applications without worrying about installing and configuring software. Containers also make it easier to share applications with other developers.
```

- Container is small,
- Virtual image is large and takes lot of space.
- Docker is not compatible with linux distro.
- While Virtual images are compatible with all.

## Installing Docker Locally

```sh
- Installing Docker on your local machine is very simple. First, you need to download and install Docker Desktop for your operating system. Once you have installed Docker Desktop, you can start using it to run containers.

- To run a container, you can use the docker run command. This command will start a new container from the specified image. To list all of the images on your machine, you can use the docker images command. To remove an image from your machine, you can use the docker rmi command.
```

```sh
docker run
```

## Images vs Containers

### Docker Image

- An executable application artifact.
- Includes app source code, but also complete environment configuration.
- Add environment variables, create directories, files etc.
- Immutable template that defines how a container will be realized.

### Docker Container

- Actually starts the application.
- A running instance of an image.
- That's when the container environment is created.
- It has its own file system, processes list, network interfaces, and other resources allocated to it

- You can run multiple containers in 1 image

## Public and Private Registries?

```sh
- A public registry is a repository that is accessible to anyone on the internet. This means that anyone can upload and download images from the registry. Public registries are often used by developers to share their code with others.

- A private registry is a repository that is only accessible to a specific group of people. This could be a group of developers working on a project, or a company that wants to keep its code private. Private registries are often used to store and manage sensitive data, such as source code or customer data.

- Here are some of the key differences between public and private registries:

* **Accessibility:** Public registries are accessible to anyone on the internet, while private registries are only accessible to a specific group of people.
* **Security:** Public registries are not as secure as private registries, as anyone can upload and download images. Private registries can be configured to require authentication, which makes them more secure.
* **Cost:** Public registries are usually free to use, while private registries may have a cost associated with them. The cost of a private registry will vary depending on the features that are offered.
```

## Docker registry?

```sh
A Docker registry is a service that stores and distributes Docker images. It is similar to a package manager for software, but instead of storing applications, it stores Docker images. Docker images are a collection of files that can be used to build a container. A container is a lightweight, self-contained unit of software that can run on any machine that has Docker installed.

There are many different Docker registries available, both public and private. Some of the most popular public registries include Docker Hub, Quay.io, and Google Container Registry. Private registries can be hosted on-premises or in the cloud.

To use a Docker registry, you need to first create an account. Once you have an account, you can upload your Docker images to the registry. You can then download your images from the registry to any machine that has Docker installed.

Docker registries make it easy to share and reuse Docker images. They are a valuable tool for developers who want to build and deploy containerized applications.
```

## Run Containers

```sh
- Pull and run containers from public repo
- Port Binding, Detached Mode etc.
```

## Create own Image (Dockerfile)?

```sh
- To create your own image, first create a file called Dockerfile. In this file, specify the base image you want to use, as well as any additional steps you want to take to build your image.
```

- To create your own Dockerfile for angular, follow these steps:

1. Open a terminal and navigate to the directory where you want to create the Dockerfile.

2. Create a new file named "Dockerfile" and open it in your preferred text editor.

3. Add the following lines to the Dockerfile:

```sh
# Use an official Node runtime as a parent image
FROM node:14-alpine

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in package.json
RUN npm install

# Run the command to start the app
CMD ["ng", "serve", "--host", "0.0.0.0"]
```

4. Save the Dockerfile and close the text editor.

5. Open a terminal and navigate to the directory where your Dockerfile is located.

6. Build the Docker image by running the following command:

```sh
docker build -t my-angular-app .
```

7. Once the image is built, run it by running the following command:

```sh
docker run -p 4200:4200 my-angular-app
```

8. The Angular application will be running on your local machine at http://localhost:4200.

- Note: Make sure that you have Angular installed on your local machine. You can install it by running the following command:
- Once you have created your Dockerfile, build your image using the following command:

```sh
npm install -g @angular/cli
```

## Main Docker Commands

```sh
- Learn Docker Commands:
- pull (docker pull name_of_image) . It pulls the image from the image registry.
- run (docker run name_of_image)
- start
- stop
- logs
- build

- docker images - Shaw the list of all docker images pulled
- docker ps - show the running docker image
- docker logs
- docker run  nginx:1.22
# Run a specific version of NGINX
- If the docker image is not installed it pulls it automatically.

- docker stop image_id

- docker run -d -p 9000:80 nginx:1.23
#This starts up a new instance of the official Nginx webserver listening to HTTP traffic on TCP port
on host's IP address :9000 mapped to internal container's port number :80
```

```sh

docker run -d nginx:1.23
# This runs an Nginx server as detached mode with port mapping
-d or --detach - It Runs the container in background and prints the container ID
```

## Image versioning?

## Docker workflow Big Picture ?

1. **Build a Docker image.** This involves creating a file called a Dockerfile, which specifies the contents of the image. The Dockerfile can include instructions to install software, copy files, and configure settings.
2. **Push the Docker image to a registry.** This is a repository where Docker images can be stored and shared. There are many different registries available, including Docker Hub, Google Cloud Registry, and Amazon ECR.
3. **Create a Docker container.** A Docker container is a runnable instance of a Docker image. To create a container, you specify the name of the image and any other options you want.
4. **Run the Docker container.** Once the container is created, you can run it by specifying the command you want to execute.

## Commands Continuations ....

```sh
docker run
- It creates a new container everytime and it does not re-use previous container.


docker ps -a
- It displays all the active containers.

docker start
- start a container without creating new containers.

docker stop
- It is used to stop the docker running container.

- One can stop a container using it's name or id

docker run --name web-app -d 9000:80 nginx:1.23
- Specifies the name of the container as web-app
```

## Docker Registry

- A service providing storage
- Docker hub is a registry.

## Dockerfile

- Dockerfile is a text document that contains commands to assemble an image
- Docker can then build an image by reading those instructions
- Dockerfiles start from a parent image or base image
- It's a Docker image that your image is based on
