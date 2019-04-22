# Stack

## Module Overview

At the end of this module, you will :

* _Learn to create a Docker stack_
* _Learn to manage a stack_
* _Learn to manage stack on Docker Swarm_

## Help

Docker is an open source and popular operating system-level virtualization (commonly known as “containerization”) technology that runs on Linux, MacOS and Windows. Docker makes it easier to create, deploy, and run applications by using containers.

A stack is a group of interrelated services that share dependencies, and can be orchestrated and scaled together. A single stack is capable of defining and coordinating the functionality of an entire application (though very complex applications may want to use multiple stacks).

Docker provide an easy command to manage each object. The default format of the command is :

```bash
docker <object> <command> <arguments>
```

The Docker command line take some parameters :
* <object> : The Docker object to manage (container, image, secret, service, etc).
* <command> : A verb defining what to do on the object.
* <arguments> : Some arguments depending on the action.

The recommended approach is to explicitly defined the object that you want to manage. In the case of container management, the recommended command is : docker stack <command>

### Exercise n°1

Get the Docker image management help information from the Docker command line.

{% tabs %}
{% tab title="Command" %}
```bash
docker stack help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Usage:	docker stack [OPTIONS] COMMAND

Manage Docker stacks

Options:
      --kubeconfig string     Kubernetes config file
      --orchestrator string   Orchestrator to use (swarm|kubernetes|all)

Commands:
  deploy      Deploy a new stack or update an existing stack
  ls          List stacks
  ps          List the tasks in the stack
  rm          Remove one or more stacks
  services    List the services in the stack

Run 'docker stack COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## External documentation

Those documentations can help you to go further in this topic :

* Docker official documentation on [stack](https://docs.docker.com/engine/swarm/swarm-tutorial/)
* Docker official documentation on [docker stack command](https://docs.docker.com/engine/reference/commandline/stack/)
* Docker official documentation on Docker stack [deployment on Docker Swarm](https://docs.docker.com/engine/swarm/stack-deploy/)
