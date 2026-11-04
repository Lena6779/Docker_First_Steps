## Docker First Steps

## What happens when you docker run the same image twice?
Docker creates two separate containers from the same image. Each has its own ID, name, and filesystem. If both try to use the same port on my computer, the second one fails with a "port is already allocated" error, so it needs a different host port.

## What happens to files created inside a container when it stops?

They stay in the stopped container and are still there if I restart it with `docker start`. They are permanently deleted when I remove the container with `docker rm`, unless they are saved in a volume. A new container from the same image won't have them. For example, `requests` is installed only in the Python container I used, not in the `python:3.11-slim` image.

## How is the -p flag used to map ports?

The format is `-p <host_port>:<container_port>`. It forwards a port on my computer to a port inside the container. With `-p 8000:8000`, I can reach the app at `localhost:8000`. With `-p 8001:8000`, I would visit `localhost:8001`, but the app would still use port 8000 inside the container.