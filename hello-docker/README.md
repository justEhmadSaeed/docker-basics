## Hello docker

In this lesson, we will learn how to :

-   [develop our first docker image](#how-to-evelop-a-docker-image)
-   [how to containerize it](#how-to-containerize-it)
-   [how to interact with it](#how-to-interact-with-it)

### How to Develop a docker image

1. Let's create a Dockerfile file in our app directory.
2. Learn about the docker keywords like FROM, WORKDIR, COPY and CMD.
3. Run the following command in t current hello-docker app directory to create our own local image.

```bash
docker build -t <tag name> PATH_TO_DOCKERFILE
# in our case
docker build -t hello-docker .
```

4. We can test our image by either confirming it from the images section of the docker desktop or run the following command:

```bash
docker images
```

### How to containerize it

1. After building our first image, we need to utilize it, to containerize our app.
2. To use our image, we can use the following command:

```bash
docker run <image-name>
# in our case
docker run hello-docker
```

3. We will see a cute `Hello Docker!` printed on our console. We will also be able to see our container in the docker desktop.

### How to interact with it

1. Sometimes we need to interact with our container to perform or monitor something, right?
2. Well, for that, we can use our container's shell to access it. The command for that is:

```bash
docker run -it hello-docker sh
```

3. `-it` stands for interactive. It will connect our terminal to the shell of our docker container, where we can do whatever we want to do.
