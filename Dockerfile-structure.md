# Structure of Dockerfile

## FROM

- Build this image from the specified image

```sh
FROM node:19-alpine
```

## COPY

- Copies local file or directory to Docker Image filesystem at given path (destination).
- While "RUN" is executed in the container, "COPY" is executed on the host.

## RUN

- Run a command in container during build time.
- Will execute any command in a shell inside the container environment.

```sh
RUN npm install
```

- Linux operating system
- Node and npm installed
- Copy application files from host into the container
- Executing "npm install", to install dependencies.

```sh
docker build -t node-app:1.0 .
```

```sh
docker run -d -p 3000:3000 node-app:1.0
```

## Steps

```sh
- Write Dockerfile
- Build Docker image
- Run as Docker container
```
