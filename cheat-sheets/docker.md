---
description: >-
  Docker is a command line interface for running commands against Docker
  clusters.
---

# Docker

Docker Community Edition (CE) is ideal for individual developers and small teams looking to get started with Docker and experimenting with container-based apps.

Docker Enterprise Edition (EE) is designed for enterprise development and IT teams who build, ship, and run business critical applications in production at scale.

## Installing

Docker can be installed on any operating systems.

{% tabs %}
{% tab title="Debian" %}
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
{% endtab %}

{% tab title="Ubuntu" %}
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
{% endtab %}

{% tab title="CentOS / RedHat" %}
```bash
sudo yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io
```
{% endtab %}

{% tab title="MacOS" %}
Docker can be installed by installing the [Docker Desktop application](https://docs.docker.com/docker-for-mac/install/).
{% endtab %}

{% tab title="Windows" %}
Docker can be installed by installing the [Docker Desktop application](https://docs.docker.com/docker-for-windows/install/).
{% endtab %}
{% endtabs %}

For further information about Docker installation method, please refer to the [Docker documentation](https://docs.docker.com/install/overview/).

## Completion

To easy manage Docker resources thanks to the command line, the shell completion can be added to the shell profile to easily navigate in command line.

```bash

```

{% hint style="info" %}
External plugins like [Docker plugin](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins#docker) for [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh) application can manage the Docker auto completion.
{% endhint %}

## Syntax

Docker is a powerful tool to manage each object on a Docker cluster. The command has a simple and unique syntax to manage everything :

```bash
docker [OPTIONS] COMMAND
```

* **options** : specifies the options that you want to be added to the command
* **command** : specifies the operation that you want to perform on one or more resources \(create, get, describe, delete\)

## Options

The following table includes short descriptions and general syntax for all Docker options :

| Options | Description |
| :--- | :--- |
| --config string | Location of client config files (default "/home/ngiron/.docker") |
| -D, --debug | Enable debug mode |
| -H, --host list | Daemon socket(s) to connect to |
| -l, --log-level string | Set the logging level ("debug"|"info"|"warn"|"error"|"fatal") (default "info") |
| --tls  | Use TLS; implied by --tlsverify |
| --tlscacert string | Trust certs signed only by this CA (default "/home/ngiron/.docker/ca.pem") |
| --tlscert string | Path to TLS certificate file (default "/home/ngiron/.docker/cert.pem") |
| --tlskey string | Path to TLS key file (default "/home/ngiron/.docker/key.pem") |
| --tlsverify | Use TLS and verify the remote |
| -v, --version | Print version information and quit |

## Management commands

The following table includes a list of all the supported management commands :

| Resource type | Description |
| :--- | :--- |
| builder | Manage builds |
| config | Manage config |
| container | Manage container |
| engine | Manage engine |
| image | Manage image |
| network | Manage network |
| node | Manage Swarm nodes |
| plugin | Manage plugin |
| secret | Manage Docker secrets |
| service | Manage service |
| stack | Manage Docker stacks |
| swarm | Manage swarm |
| system | Manage system |
| trust | Manage trust on Docker images |
| volume | Manage volume |

## Commands

The following table includes a list of all the supported commands :

| Resource type | Description |
| :--- | :--- |
| attach | Attach local standard input, output, and error streams to a running container |
| build | Build an image from a Dockerfile |
| commit | Create a new image from a container's changes |
| cp | Copy files/folders between a container and the local filesystem |
| create | Create a new container |
| deploy | Deploy a new stack or update an existing stack |
| diff | Inspect changes to files or directories on a container's filesystem |
| events | Get real time events from the server |
| exec | Run a command in a running container |
| export | Export a container's filesystem as a tar archive |
| history | Show the history of an image |
| images | List images |
| import | Import the contents from a tarball to create a filesystem image |
| info | Display system-wide information |
| inspect | Return low-level information on Docker objects |
| kill | Kill one or more running containers |
| load | Load an image from a tar archive or STDIN |
| login | Log in to a Docker registry |
| logout | Log out from a Docker registry |
| logs | Fetch the logs of a container |
| pause | Pause all processes within one or more containers |
| port | List port mappings or a specific mapping for the container |
| ps |  List containers |
| pull | Pull an image or a repository from a registry |
| push | Push an image or a repository to a registry |
| rename | Rename a container |
| restart | Restart one or more containers |
| rm | Remove one or more containers |
| rmi | Remove one or more images |
| run | Run a command in a new container |
| save | Save one or more images to a tar archive (streamed to STDOUT by default) |
| search | Search the Docker Hub for images |
| start | Start one or more stopped containers |
| stats | Display a live stream of container(s) resource usage statistics |
| stop | Stop one or more running containers |
| tag | Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE |
| top | Display the running processes of a container |
| unpause | Unpause all processes within one or more containers |
| update | Update configuration of one or more containers |
| version | Show the Docker version information |
| wait | Block until one or more containers stop, then print their exit codes |

## Docker registry

A set of command line to manage Docker registry.

```bash
# Log Docker to DockerHub registry
docker login

# Log Docker to a localhost registry
docker login localhost:8080

# Search nginx images on default Docker registry
docker search nginx

# Search nginx images on default Docker registry with some filters
docker search nginx --stars=3 --no-trunc busybox

# Pull an nginx image from the default Docker registry
docker pull nginx

# Pull an image from a local Docker registry
docker pull eon01/nginx localhost:5000/myadmin/nginx

# Push the local Docker image mydockerimage/nginx to the default Docker registry
docker push mydockerimage/nginx

# Push an image to the a local Docker registry
docker push mydockerimage/nginx localhost:5000/myadmin/nginx
```

## Docker image

A set of command line to manage Docker image.

```bash
# Pull an nginx image from the default Docker registry
docker pull nginx

# Pull an image from a local Docker registry
docker pull eon01/nginx localhost:5000/myadmin/nginx

# Push the local Docker image mydockerimage/nginx to the default Docker registry
docker push mydockerimage/nginx
```

## Docker container

A set of command line to manage Docker container.

```bash
# Create an nginx Docker container
docker container create nginx --name nginx

# Run an nginx Docker container and automatically connect to it
docker container create -t -i nginx --name nginx

# Run an nginx Docker container but don't kill it when exit
docker container run -it --name nginx -d nginx

# Rename an nginx container
docker container rename nginx webserver

# Update a container
docker container update --cpu-shares 512 -m 300M infinite

# Get running containers
docker container ls

# Get tasks of a container
docker container ps webserver

# Get each running container identifier
docker container ps -q

# Get each container (running and stopped)
docker container ps -a

# Inspect the configuration of a container
docker container inspect webserver

# Get the IP address of each running container
docker container inspect --format '{{ .NetworkSettings.IPAddress }}' $(docker container ps -q)

# Remove a container named webserver
docker container rm webserver

# Start a container
docker container start nginx

# Restart a container
docker container restart nginx

# Stop a container
docker container stop nginx

# Kill a container with a SIGKILL
docker container kill nginx
```

## Docker volume

A set of command line to manage Docker volume.

```bash
# Create a new volume named hello
docker volume create hello

# Create a container which consume the new created volume
docker run -d -v hello:/world busybox ls /world

# List existing Docker volume
docker volume ls

# Inspect Docker volume named hello
docker volume inspect hello

# Remove all unused Docker volumes
docker volume prune

# Delete a volume named hello
docker volume rm hello
```

## Docker network

A set of command line to manage Docker network.

```bash
# Create a new bridge network named my-bridge-network
docker network create -d bridge my-bridge-network

# Create a new overlay network named MyOverlayNetwork
docker network create -d overlay MyOverlayNetwork

# Create a new overlay network named MyCustomOverlayNetwork
docker network create -d overlay \
  --subnet=192.168.0.0/16 \
  --subnet=192.170.0.0/16 \
  --gateway=192.168.0.100 \
  --gateway=192.170.0.100 \
  --ip-range=192.168.1.0/24 \
  --aux-address="my-router=192.168.1.5" --aux-address="my-switch=192.168.1.6" \
  --aux-address="my-printer=192.170.1.5" --aux-address="my-nas=192.170.1.6" \
  MyCustomOverlayNetwork

# List all existing networks
docker network ls

# Get information about a network named mysimplenetwork
docker network inspect mysimplenetwork

# Connect a running nginx container to an existing network named MyOverlayNetwork
docker network connect MyOverlayNetwork nginx

# Create an nginx container and automatically connect it to the MyOverlayNetwork network
docker run -it -d --network=MyOverlayNetwork nginx

# Disconnect a running container from a network
docker network disconnect MyOverlayNetwork nginx

# Delete a network named MyOverlayNetwork
docker network rm MyOverlayNetwork
```

## Docker stack

A set of command line to manage Docker stack.

```bash
# Create a stack named vossibility on a docker compose file definition
docker stack deploy --compose-file docker-compose.yml vossibility

# List all running stack
docker stack ls

# List all tasks of vossibility stack
docker stack ps vossibility

# Delete a stack named vossibility
docker stack rm vossibility
```

## Docker swarm

A set of command line to manage Docker Swarm cluster.

```bash
# Initialize the master node on a specific IP address
docker swarm init --advertise-addr 192.168.10.1

# Get the token for a manager node
docker swarm join-token manager

# Get the token for a worker node
docker swarm join-token worker

# Join a node based on a token
docker swarm join --token SWMTKN-1-3pu6hszjas19xyp7ghgosyx9k8atbfcr8p2is99znpy26u2lkl-1awxwuwd3z9j1z3puu7rcgdbx 192.168.99.121:2377

# List all nodes
docker node ls

# Promote the node named NODE_NAME as manager
docker node promote NODE_NAME

# Leave the current node from a Swarm cluster.
docker swarm leave
```

## Docker service

A set of command line to manage Docker service.

```bash
# Create a service named vote based on the instavote/vote image and expose the port 8080
docker service create --name vote -p 8080:80 instavote/vote

# List all running services
docker service ls

# List the tasks of a running service
docker service ps SERVICE_NAME

# Get all the logs of a service named SERVICE_NAME
docker service logs SERVICE_NAME

# Scale the service named vote to 3
docker service scale vote=3

# Update the image of an existing service named vote
docker service update --image instavote/vote:movies vote

# Force a service to be reloaded and define the update strategy
docker service update --force --update-parallelism 1 --update-delay 30s nginx

# Update the CPU limits of the nginx container
docker service update --limit-cpu 2 nginx

# Update the number of replicas of the nginx container
docker service update --replicas=5 nginx

# Delete a service name vote
docker service rm vote
```

## Other information

#### Stats

Print stats of running Docker containers.

```bash
# Show stats of running containers.
docker stats
```

#### Top

Print stats on processes of Docker container.

```bash
# Show processes of container.
docker top CONTAINER_NAME
```

#### Version

Print the client and server version information.

```bash
# Show the Docker version information
docker version

# Show the Docker Server version information
docker version --format '{{.Server.Version}}'
```

## External documentation

To go further in the management of Docker, please refer to these documentations :

* [Docker documentation](https://docs.docker.com/)
* [Docker blog](https://blog.docker.com/)
* [Docker get started tutorials](https://docs.docker.com/get-started/)
* [Docker official documentation to install Docker Desktop on Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
* [Docker official documentation to install Docker Desktop on MacOS](https://docs.docker.com/docker-for-mac/install/)
* [Docker official documentation to install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)
* [Docker official command description](https://docs.docker.com/engine/reference/commandline/docker/)
