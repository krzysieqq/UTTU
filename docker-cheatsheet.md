#Docker
```bash
docker ps # is a command to list containers.
    -a # shows all containers (without -a flag ps will show only running containers).
docker logs -f <id/name>  # Fetches the logs of a container.
docker rm -f $(docker ps -aq) # Remove all containers
docker rm $(docker ps -q -f status=exited) # Remove all containers with status=exited
docker stop $(docker ps -q) # will run stop only for active
docker stop $(docker ps -aq) # will run stop for all
docker run # command to run a container
    -t # flag assigns a pseudo-tty or terminal inside the new container.
    -i # flag allows you to make an interactive connection by grabbing the standard input (STDIN) of the container.
    --rm # flag to automatically remove the container when the process exits.
docker inspect <id/name> # Displays system wide information about the Docker
docker inspect --format '{{ .NetworkSettings.IPAddress }}' CONTAINER_ID # Find a container IP Address


Backup:
docker exec -t -u postgres your-db-container pg_dumpall -c > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql

Restore:
cat your_dump.sql | docker exec -i your-db-container psql -Upostgres

# ------------------------------------
# Docker alias and function
# ------------------------------------

# Get latest container ID
alias dl="docker ps -l -q"

# Get container process
alias dps="docker ps"

# Get process included stop container
alias dpa="docker ps -a"

# Get images
alias di="docker images"

# Get container IP
alias dip="docker inspect --format '{{ .NetworkSettings.IPAddress }}'"

# Run deamonized container, e.g., $dkd base /bin/echo hello
alias dkd="docker run -d -P"

# Run interactive container, e.g., $dki base /bin/bash
alias dki="docker run -i -t -P"

# Execute interactive container, e.g., $dex base /bin/bash
alias dex="docker exec -i -t"

# Stop all containers
dstop() { docker stop $(docker ps -a -q); }

# Remove all containers
drm() { docker rm $(docker ps -a -q); }

# Stop and Remove all containers
alias drmf='docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)'

# Remove all images
dri() { docker rmi $(docker images -q); }

# Dockerfile build, e.g., $dbu tcnksm/test 
dbu() { docker build -t=$1 .; }

# Show all alias related docker
dalias() { alias | grep 'docker' | sed "s/^\([^=]*\)=\(.*\)/\1 => \2/"| sed "s/['|\']//g" | sort; }

# Bash into running container
dbash() { docker exec -it $(docker ps -aqf "name=$1") bash; }


```
