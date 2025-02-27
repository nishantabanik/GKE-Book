## Important commands in Docker

We will quickly get acquainted with the common commands that you need to know to use Docker. These commands are as follows:

Docker run: To create a container from an image.

```
docker run nginx
```

Docker ps: Gives a list of all running containers

```
docker ps --all
```

Docker stop: This command is used to stop a running container.

```
docker stop container_id
```

Docker images: Lists all available images.

```
docker images
```

Docker rm: This command is used to remove a Docker container.

```
docker rm container_id
```

Docker pull: This command is used to download a Docker image from a registry.

```
docker pull nginx
```

Docker network ls: This command is used to know the details of the list of networks in the cluster.

```
docker network ls
```

Docker logs: This command is used to check the logs of all the docker containers.

```
docker logs container_id
```

Docker exec: This command is used to execute a command in a running container.

```
docker exec -it container_id bash
```

Docker compose: This command is used to manage multi-container Docker applications. You define the configuration of your application's services, networks, and volumes in a file called `docker-compose.yml`, and then use the docker-compose command to start and stop your application.

```
docker-compose up
```

```
docker-compose down
```
