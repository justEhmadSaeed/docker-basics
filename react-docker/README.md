# Host React app with Docker

In this lesson, we will learn about:

-   RUN, USER and EXPOSE keywords
-   How to expose a port to the container
-   [How to do Port mapping](#port-mapping)
-   [How to publish our docker image to Docker Hub](#publish-our-docker-image)

Check out the Dockerfile in this directory with self-explanatory comments.

## Port Mapping

-   To build the image:

```bash
docker build -t react-docker .
```

-   To start the container:

```bash
docker run -p 5173:5173 react-docker
```

-   This container won't be listening to the changes in our code. To make it listen to our local code changes, we need to mount the current directory into the app directory of the container.
    -v stands for volume which containers use to store data. `pwd` represents the directory where the below command will be executed. The next /app/node_modules will create a volume for node_modules, so we don't have to install them every time, we re-run the container.

```bash
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker
```

## Publish Our Docker Image

-   To make our image accessible over the internet, we have to upload it to the [Docker Hub](https://hub.docker.com/). For that, we first need to tag our image with the following command:

```bash
docker tag <image-source>:<tag> <username>/<image-name>:<tag>
# in our case
docker tag react-docker ehmadsaeed/react-docker
```

We didn't specify a tag here, so it will be tagged `latest` by default.

-   To publish that image, we first need to login with our Docker Hub credentials via the terminal.

```bash
docker login
```

-   Then, push our image to Docker Hub. We can see it under the repositories section of our Docker Hub portal.

```bash
docker push ehmadsaeed/react-docker
```

## Common Commands

-   To enlist the running containers, we can use the following command:

```bash
docker ps
```

-   We can use the container ID from the above command to stop that container.

```bash
docker stop <container-id>
```

-   To stop all running containers at once:

```bash
docker container prune
```

-   To remove a specific container (use `--force` for running containers):

```bash
docker rm <container-id>
```

-   We use a `.dockerignore` file to prevent specific files/ directories from pushing to the docker, just like `.gitignore`.

## Next Steps

Tired of remembering and writing all these lengthy commands? Don't worry. It's good to know the basics of Docker commands in the beginning. Anyhow, how about composing all of these settings into a single and simple command? Here comes the next [Automating the Containerization](/compose-docker/README.md) step.
