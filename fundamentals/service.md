# Service

## Module Overview

At the end of this module, you will :

* _Learn to create a service_
* _Learn to expose a container_
* _Learn to manage container access_

## Help

Docker is an open source and popular operating system-level virtualization (commonly known as “containerization”) technology that runs on Linux, MacOS and Windows. Docker makes it easier to create, deploy, and run applications by using containers.

TODOOOOOOOOOOO

Docker provide an easy command to manage each object. The default format of the command is :

```bash
docker <object> <command> <arguments>
```

The Docker command line take some parameters :
* <object> : The Docker object to manage (container, image, secret, service, etc).
* <command> : A verb defining what to do on the object.
* <arguments> : Some arguments depending on the action.

The recommended approach is to explicitly defined the object that you want to manage. In the case of container management, the recommended command is : docker service <command>

### Exercise n°1

Get the Docker image management help information from the Docker command line.

{% tabs %}
{% tab title="Command" %}
```bash
docker service help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Usage:	docker service COMMAND

Manage services

Commands:
  create      Create a new service
  inspect     Display detailed information on one or more services
  logs        Fetch the logs of a service or task
  ls          List services
  ps          List the tasks of one or more services
  rm          Remove one or more services
  rollback    Revert changes to a service\'s configuration
  scale       Scale one or multiple replicated services
  update      Update a service

Run 'docker service COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## External documentation

Those documentations can help you to go further in this topic :

* Docker official documentation on [service](https://docs.docker.com/engine/swarm/how-swarm-mode-works/services/)
* Docker official documentation on [docker service command](https://docs.docker.com/engine/reference/commandline/service/)
