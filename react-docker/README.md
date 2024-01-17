# Host React app with Docker

In this lesson, we will learn about:

-   RUN, USER and EXPOSE keywords
-   How to expose a port to the container
-   [Docker Volume](#docker-volume)
-   [How to do Port mapping](#port-mapping)
-   [How to publish our docker image to Docker Hub](#publish-our-docker-image)

Check out the Dockerfile in this directory with self-explanatory comments.

## Docker Volume

Imagine a shared cookbook that everyone in your family uses 📚:

In your family, there's a cookbook (Docker volume) that contains all the favorite recipes. Each member of the family can access this cookbook to add new recipes or make notes. The cookbook is a central, shared storage space that ensures everyone has the same set of recipes, and changes made by one person are reflected for everyone.

In Docker terms, a volume is like a shared storage space that containers can use to persist data. It's a way for containers to share and store information, ensuring consistency and accessibility. Volumes are not tied to a specific container; instead, they act as a central storage location that can be accessed by multiple containers.

Just as the cookbook allows everyone in the family to share and update recipes, Docker volumes enable containers to share and persist data, making it accessible to other containers and ensuring data consistency across the Docker environment. 📚🐳

## Port Mapping

Let's compare port mapping in Docker to a reception desk at a busy office building 🏢:

Imagine your office building has a central reception desk (host machine) that handles incoming calls and directs them to the appropriate offices. Each office (Docker container) has its own extension number (container's internal port), and the receptionist (Docker daemon) manages the flow of calls.

Now, let's relate this to Docker port mapping. In a Dockerized application, a container might be running a web server on its own internal port, like port 80. However, to make that web server accessible from the outside world, you need to map a port on the host machine to the internal port of the container.

So, it's like telling the receptionist, "Hey, if someone calls the main office number (host machine's IP) and asks for the marketing department (external port), forward the call to the corresponding office extension (container's internal port 80)."

In Docker, when you run a container, you can use the -p flag to map a port on your host machine to a port in the container. For example:

```bash
docker run -p 8080:80 my-web-app
```

In essence, Docker port mapping allows external traffic to find its way to the correct services inside the containers, just like calls finding their way to the right offices through the reception desk in our office analogy. 📞🐳

Now, for our current app:

-   Build the image:

```bash
docker build -t react-docker .
```

-   Start the container with port mapping:

```bash
docker run -p 5173:5173 react-docker
```

-   This container won't be listening to the changes in our code. To make it listen to our local code changes, we need to mount the current directory into the app directory of the container. `-v` stands for volume which containers use to store data. `pwd` represents the directory where the below command will be executed. The next /app/node_modules will create a volume for node_modules, so we don't have to install them every time, we re-run the container.

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
