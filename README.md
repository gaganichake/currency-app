# currency-app

# Docker commands

Run a docker image
Docker run -p 5000:500 project/app-name:1.0.0.RELEASE

-p : port number. {Host Posr}:{Container Port}
-d : Run the container in the background
--restart=always : Automatically Start the application container when starting docker
-m 512m : How much maximum memory you want to allocate to this container
--cpu-quota: How much CPU Quota you want to allocate tooth’s specific container. Max is 100%

View docker logs
Docker log

Show only running containers
Docker container ls

Show running containers as well as stopped containers
Docker container ls -a

Show all docker images
Docker images

Stop a running container gracefully
Docker container stop

Create tag for existing docker repository
Docker tag project/app-name:1.0.0.RELEASE project/app-name:latest

Only download the image with “latest” tag. “latest” is default tag, if not specified
Docker pull project/app-name

Search an image on Docker Hub
Docker search mysql

Show difference layers of a docker image when created
Docker image history <image ID or repository name>

Detailed in-depth information of an image
Docker image inspect <image ID or repository name>

Remove a docker image from local machine - not from registry.
Docker image remove <image ID or repository name>

Pause a running container
Docker container pause <image ID or repository name>
Docker container unpause <image ID or repository name>

Detailed in-depth information of a container
Docker container inspect <image ID or repository name>

Remove all stopped containers from local machine.
Docker container prune

Show container logs
Docker container log -f <image ID or repository name>

Stop a running container forcefully
Docker container kill <image ID or repository name>

See all events happening behind the scene in a Docker environment
Docker events

Display the running top processes of a running container - PID, Use, Time, Command
Docker top <image ID or repository name>

Show all the stats of all running container - Container ID/Name, CPU, Memory Usage/Limit, I/O, PIDS
Docker stats

See all resource being manager by docker system
Docker system df