#Docker
```bash
docker ps # is a command to list containers.
    -a # shows all containers (without -a flag ps will show only running containers).
docker logs -f <id/name>  # Fetches the logs of a container.
docker rm -f $(docker ps -aq) # Remove all containers
docker run # command to run a container
    -t # flag assigns a pseudo-tty or terminal inside the new container.
    -i # flag allows you to make an interactive connection by grabbing the standard input (STDIN) of the container.
    --rm # flag to automatically remove the container when the process exits.
docker inspect <id/name> # Displays system wide information about the Docker
```