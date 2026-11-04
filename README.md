# Docker First Steps

A beginner Docker practice project. It covers running containers, building an image for a small FastAPI app, and managing containers and images from the command line.

## Project Files

| File | Purpose |
|---|---|
| `app.py` | FastAPI app with one `GET /` endpoint |
| `Dockerfile` | Instructions for building the app's image |
| `answers.md` | Written answers to the assignment questions |

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running

## Run the App

Build the image:

```powershell
docker build -t my-first-api .
```

Start a container:

```powershell
docker run -p 8000:8000 my-first-api
```

Then visit [http://localhost:8000](http://localhost:8000). You should see:

```json
{"message":"Hello from Docker!"}
```

To stop the app, press `Ctrl+C` in the terminal or run `docker stop <id>` from a second terminal.

## Docker Commands Practiced

| Command | What it does |
|---|---|
| `docker run hello-world` | Runs a test container to verify Docker is working |
| `docker run -it python:3.11-slim bash` | Opens an interactive shell inside a Python container |
| `docker build -t my-first-api .` | Builds an image from the `Dockerfile` in the current folder |
| `docker run -p 8000:8000 my-first-api` | Runs the app and maps port 8000 on the computer to port 8000 in the container |
| `docker ps` | Lists running containers |
| `docker ps -a` | Lists all containers, including stopped ones |
| `docker images` | Lists images on the computer |
| `docker stop <id>` | Stops a running container |
| `docker rm <id>` | Removes a stopped container |

## What I Learned

- An image is a template, and a container is a running instance of that image.
- Running the same image twice creates two separate containers.
- Files created in a container are deleted when the container is removed, unless they are saved in a volume.
- The `-p` flag uses the format `-p <host_port>:<container_port>`.
- An app in a container must listen on `0.0.0.0` to be reachable from outside the container.
- After changing the `Dockerfile` or app code, the image must be rebuilt for the changes to take effect.

## Extra Note
When I ran `hello-world` twice, I got two new containers with different IDs and names.