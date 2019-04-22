# Node

## Module Overview

At the end of this module, you will :

* _Learn to demote manager node_
* _Learn to update Docker node_
* _Learn to promote a worker node_

## Help

Docker is an open source and popular operating system-level virtualization (commonly known as “containerization”) technology that runs on Linux, MacOS and Windows. Docker makes it easier to create, deploy, and run applications by using containers.

Docker Engine 1.12 introduces swarm mode that enables administrator to create a cluster of one or more Docker Engines called a swarm. A swarm consists of one or more nodes: physical or virtual machines running Docker Engine 1.12 or later in swarm mode.

Docker provide an easy command to manage each object. The default format of the command is :

```bash
docker <object> <command> <arguments>
```

The Docker command line take some parameters :
* <object> : The Docker object to manage (container, image, secret, service, etc).
* <command> : A verb defining what to do on the object.
* <arguments> : Some arguments depending on the action.

The recommended approach is to explicitly defined the object that you want to manage. In the case of container management, the recommended command is : docker node <command>

### Exercise n°1

Get the Docker image management help information from the Docker command line.

{% tabs %}
{% tab title="Command" %}
```bash
docker node help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Usage:	docker node COMMAND

Manage Swarm nodes

Commands:
  demote      Demote one or more nodes from manager in the swarm
  inspect     Display detailed information on one or more nodes
  ls          List nodes in the swarm
  promote     Promote one or more nodes to manager in the swarm
  ps          List tasks running on one or more nodes, defaults to current node
  rm          Remove one or more nodes from the swarm
  update      Update a node

Run 'docker node COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## External documentation

Those documentations can help you to go further in this topic :

* Docker official documentation on [node](https://docs.docker.com/engine/swarm/how-swarm-mode-works/nodes/)
* Docker official documentation on [docker node command](https://docs.docker.com/engine/reference/commandline/node/)
