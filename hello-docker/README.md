# Hello docker 🐳

In this lesson, we will learn:

-   [Docker Image](#docker-image)
-   [Docker Container](#docker-container)
-   [develop our first docker image](#how-to-evelop-a-docker-image)
-   [how to containerize it](#how-to-containerize-it)
-   [how to interact with it](#how-to-interact-with-it)

Let's use simple analogies to describe Docker images and Docker containers:

## Docker Image:

Analogous to a recipe or blueprint for baking cookies 🍪:

Imagine you have a recipe that specifies all the ingredients and steps needed to bake delicious cookies. The recipe itself is like a Docker image. It contains instructions on what ingredients (dependencies and configurations) to use and how to combine them. You can make multiple batches of cookies (containers) using the same recipe (image), ensuring consistency and reproducibility.

In the Docker world, an image is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, including the code, runtime, libraries, and system tools.

## Docker Container

Think of a Docker container as an instance of your baked cookies 🍪:

Once you have your cookie recipe (Docker image), you can create multiple batches of cookies (containers) by following the instructions in the recipe. Each batch is separate and self-contained. Similarly, a Docker container is an instantiated runtime environment created from a Docker image. It encapsulates the application and its dependencies, running in an isolated and reproducible environment.

Containers are like individual batches of cookies - you can make many of them from the same recipe, and each batch is independent, portable, and runs consistently, just like Docker containers with their images.

## How to Develop a Docker Image

1. Let's create a Dockerfile file in our app directory.
2. Learn about the docker keywords like FROM, WORKDIR, COPY, and CMD.
3. Run the following command in the current hello-docker app directory to create our own local image.

```bash
docker build -t <tag name> PATH_TO_DOCKERFILE
# in our case
docker build -t hello-docker .
```

4. We can test our image by either confirming it from the images section of the docker desktop or running the following command:

```bash
docker images
```

## How to containerize it

1. After building our first image, we need to utilize it, to containerize our app.
2. To use our image, we can use the following command:

```bash
docker run <image-name>
# in our case
docker run hello-docker
```

3. We will see a cute `Hello Docker!` printed on our console. We will also be able to see our container in the docker desktop.

## How to interact with it

1. Sometimes we need to interact with our container to perform or monitor something, right?
2. Well, for that, we can use our container's shell to access it. The command for that is:

```bash
docker run -it hello-docker sh
```

3. `-it` stands for interactive. It will connect our terminal to the shell of our docker container, where we can do whatever we want to do.

## Next Steps

Now, we will use our existing knowledge to [Dockerize our React app](/react-docker/README.md) and learn about concepts like Docker Volumes and port mapping.
