# Automate Dockerization

In this lesson, we will learn about:

-   How to automate the containerization process
-   How to use Docker compose file

## Automate Containerization Process

Well, it might be hard for us to write so lengthy commands repeatedly. How about automating all of that stuff?

1. Create a new React project. Enter the docker initialization command in the project directory.

```bash
docker init
```

2. It will create `.dockerignore`, `Dockerfile` and `compose.yaml` files in the root directory. We are already familiar with the first two files. Let's replace the `Dockerfile` from [Our React Docker Project](/react-docker/Dockerfile).

3. The previous command to run React Docker can be translated in the `compose.yaml` syntax as such:

```bash
# previous command
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker
```

```bash
# compose.yaml
services:
  web:
    build:
      context: .
    ports:
      - 5173:5173
    volumes:
      - .:/app
      - /app/node_modules
```

4. Now, we just need a simple command to build and run the container. It's that simple now. Isn't that great?

```bash
docker compose up
```
