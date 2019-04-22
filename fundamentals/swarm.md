# Swarm

## Module Overview

At the end of this module, you will :

* _Learn to create a Docker Swarm cluster_
* _Learn to manage Docker Swarm master nodes_
* _Learn to manage Docker Swarm worker nodes_

## Help

Docker is an open source and popular operating system-level virtualization (commonly known as “containerization”) technology that runs on Linux, MacOS and Windows. Docker makes it easier to create, deploy, and run applications by using containers.

A swarm is a group of machines that are running Docker and joined into a cluster. After that has happened, the usual Docker command still work but they are executed on a cluster by a swarm manager. The machines in a swarm can be physical or virtual. After joining a swarm, they are referred to as nodes.

Docker provide an easy command to manage each object. The default format of the command is :

```bash
docker <object> <command> <arguments>
```

The Docker command line take some parameters :
* <object> : The Docker object to manage (container, image, secret, service, etc).
* <command> : A verb defining what to do on the object.
* <arguments> : Some arguments depending on the action.

The recommended approach is to explicitly defined the object that you want to manage. In the case of container management, the recommended command is : docker swarm <command>

### Exercise n°1

Get the Docker image management help information from the Docker command line.

{% tabs %}
{% tab title="Command" %}
```bash
docker swarm help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Usage:	docker swarm COMMAND

Manage Swarm

Commands:
  ca          Display and rotate the root CA
  init        Initialize a swarm
  join        Join a swarm as a node and/or manager
  join-token  Manage join tokens
  leave       Leave the swarm
  unlock      Unlock swarm
  unlock-key  Manage the unlock key
  update      Update the swarm

Run 'docker swarm COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## External documentation

Those documentations can help you to go further in this topic :

* Docker official documentation on [swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/)
* Docker official documentation on [docker swarm command](https://docs.docker.com/engine/reference/commandline/swarm/)
