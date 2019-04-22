# Secret

## Module Overview

At the end of this module, you will :

* _Learn to create a Docker secret_
* _Learn to manage sensitive data_
* _Learn to attach a secret to a container_

## Help

Docker is an open source and popular operating system-level virtualization (commonly known as “containerization”) technology that runs on Linux, MacOS and Windows. Docker makes it easier to create, deploy, and run applications by using containers.

A secret is a blob of data, such as a password, SSH private key, SSL certificate, or another piece of data that should not be transmitted over a network or stored unencrypted in a Dockerfile or in your application’s source code.

Docker provide an easy command to manage each object. The default format of the command is :

```bash
docker <object> <command> <arguments>
```

The Docker command line take some parameters :
* <object> : The Docker object to manage (container, image, secret, service, etc).
* <command> : A verb defining what to do on the object.
* <arguments> : Some arguments depending on the action.

The recommended approach is to explicitly defined the object that you want to manage. In the case of container management, the recommended command is : docker secret <command>

### Exercise n°1

Get the Docker image management help information from the Docker command line.

{% tabs %}
{% tab title="Command" %}
```bash
docker secret help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Usage:	docker secret COMMAND

Manage Docker secrets

Commands:
  create      Create a secret from a file or STDIN as content
  inspect     Display detailed information on one or more secrets
  ls          List secrets
  rm          Remove one or more secrets

Run 'docker secret COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## External documentation

Those documentations can help you to go further in this topic :

* Docker official documentation on [secret](https://docs.docker.com/engine/swarm/secrets/)
* Docker official documentation on [docker secret command](https://docs.docker.com/engine/reference/commandline/secret/)
