# Host React app with Docker

In this lesson, we will learn about:

-   RUN, USER and EXPOSE keywords
-   How to expose a port to the container
-   How to do Port mapping

Check out the Dockerfile in this directory with self-explanatory comments.

## Commands

-   To build the image:

```bash
docker build -t react-docker .
```

-   To start the container:

```bash
docker run -p 5173:5173 react-docker
```

-   To enlist the running containers, we can use the following command:

```bash
docker ps
```

-   We can use the container id from the above command to stop that container.

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

-   We use `.dockerignore` file to prevent specific files/ directories from pushing to the docker, just like `.gitignore`.
