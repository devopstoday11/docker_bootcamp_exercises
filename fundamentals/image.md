# Image

## Module Overview

At the end of this module, you will :

* _Learn to build an image_
* _Learn to tag an image_
* _Learn to share an image_

## Help

Docker is an open source and popular operating system-level virtualization (commonly known as “containerization”) technology that runs on Linux, MacOS and Windows. Docker makes it easier to create, deploy, and run applications by using containers.

Docker can package application dependencies and binaries in, what is called, docker image. It can be used across multiple environments without having to manage any dependency.

Once an application is package in an image, Docker can run it in an isolated container. The isolation and the image management allow different version of an application to be deployed on the same host.

Docker provide an easy command to manage each object. The default format of the command is :

```bash
docker <object> <command> <arguments>
```

The Docker command line take some parameters :
* <object> : The Docker object to manage (container, image, secret, service, etc).
* <command> : A verb defining what to do on the object.
* <arguments> : Some arguments depending on the action.

The recommended approach is to explicitly defined the object that you want to manage. In the case of container management, the recommended command is : docker image <command>

### Exercise n°1

Get the Docker image management help information from the Docker command line.

{% tabs %}
{% tab title="Command" %}
```bash
docker image help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Usage:	docker image COMMAND

Manage images

Commands:
  build       Build an image from a Dockerfile
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Display detailed information on one or more images
  load        Load an image from a tar archive or STDIN
  ls          List images
  prune       Remove unused images
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rm          Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

Run 'docker image COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## Search

## Pull

## Create



#### Exercise n°1

Create a Dockerfile with that content :

{% code-tabs %}
{% code-tabs-item title="/data/image/Dockerfile" %}
```

```
{% endcode-tabs-item %}
{% endcode-tabs %}

Create the resource based on the previous yaml definition file.

```bash
docker build -t myfirstimage /data/image/Dockerfile
```

## Get

The _get_ command list the object asked. It could be a single object or a list of multiple objects comma separated. This command is useful to get the status of each object. The output can be formatted to only display some information based on some json search or external tools like `tr`, `sort`, `uniq`.

The default output display some useful information about each services :

* Repository : the name of the Docker image
* Tag : the tag of the Docker image
* Image Id : the unique identifier of the Docker image
* Created :  the age of the object since his creation
* Size : the size of the Docker image

#### Exercise n°1

List all existing Images.

{% tabs %}
{% tab title="Command" %}
```bash
docker images
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
REPOSITORY           TAG                 IMAGE ID            CREATED             SIZE
wordpress            latest              05e305efac8d        27 hours ago        421MB
```
{% endtab %}
{% endtabs %}

## Inspect

Once an object is running, it is inevitably a need to debug problems or check the configuration deployed.

The _inspect_ command display a lot of configuration information about the Images \(labels, tags, name, Id, etc.\).

This command is really useful to introspect and debug an object deployed in a cluster.

#### Exercise  n°1

Inspect one of the existing Image.

{% tabs %}
{% tab title="Command" %}
```bash
docker image inspect 05e305efac8d
```
{% endtab %}

{% tab title="CLI Return" %}
```text
[
    {
        "Id": "sha256:05e305efac8dd4cde13c1e3f5aba669d2e890af0e71947fbde4fddee082d714c",
        "RepoTags": [
            "wordpress:latest"
        ],
        "RepoDigests": [
            "wordpress@sha256:23315cb9ae3f20b7b17de4a39995b9bc735f898f859f52d5586f8f173872d6b8"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2019-03-11T23:30:00.210887805Z",
        "Container": "20d3d4c8991686cbce58643ae1f6f9bc60b57d12007fbe5d9164306855a15d33",
        "ContainerConfig": {
            "Hostname": "20d3d4c89916",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "PHPIZE_DEPS=autoconf \t\tdpkg-dev \t\tfile \t\tg++ \t\tgcc \t\tlibc-dev \t\tmake \t\tpkg-config \t\tre2c",
                "PHP_INI_DIR=/usr/local/etc/php",
                "APACHE_CONFDIR=/etc/apache2",
                "APACHE_ENVVARS=/etc/apache2/envvars",
                "PHP_EXTRA_BUILD_DEPS=apache2-dev",
                "PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2 --disable-cgi",
                "PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2",
                "PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2",
                "PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie",
                "GPG_KEYS=1729F83938DA44E27BA0F4D3DBDB397470D12172 B1B44D8F021E4E2D6021E995DC9FF8D3EE5AF27F",
                "PHP_VERSION=7.2.16",
                "PHP_URL=https://secure.php.net/get/php-7.2.16.tar.xz/from/this/mirror",
                "PHP_ASC_URL=https://secure.php.net/get/php-7.2.16.tar.xz.asc/from/this/mirror",
                "PHP_SHA256=7d91ed3c1447c6358a3d53f84599ef854aca4c3622de7435e2df115bf196e482",
                "PHP_MD5=",
                "WORDPRESS_VERSION=5.1",
                "WORDPRESS_SHA1=830eadf0afa15928d7f6856b1b85bf57b8e1f585"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "#(nop) ",
                "CMD [\"apache2-foreground\"]"
            ],
            "ArgsEscaped": true,
            "Image": "sha256:0e68fcd954487398fcfc5b0b510a0c76deee2d7f547030f233d81064242d9962",
            "Volumes": {
                "/var/www/html": {}
            },
            "WorkingDir": "/var/www/html",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {}
        },
        "DockerVersion": "18.06.1-ce",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "PHPIZE_DEPS=autoconf \t\tdpkg-dev \t\tfile \t\tg++ \t\tgcc \t\tlibc-dev \t\tmake \t\tpkg-config \t\tre2c",
                "PHP_INI_DIR=/usr/local/etc/php",
                "APACHE_CONFDIR=/etc/apache2",
                "APACHE_ENVVARS=/etc/apache2/envvars",
                "PHP_EXTRA_BUILD_DEPS=apache2-dev",
                "PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2 --disable-cgi",
                "PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2",
                "PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2",
                "PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie",
                "GPG_KEYS=1729F83938DA44E27BA0F4D3DBDB397470D12172 B1B44D8F021E4E2D6021E995DC9FF8D3EE5AF27F",
                "PHP_VERSION=7.2.16",
                "PHP_URL=https://secure.php.net/get/php-7.2.16.tar.xz/from/this/mirror",
                "PHP_ASC_URL=https://secure.php.net/get/php-7.2.16.tar.xz.asc/from/this/mirror",
                "PHP_SHA256=7d91ed3c1447c6358a3d53f84599ef854aca4c3622de7435e2df115bf196e482",
                "PHP_MD5=",
                "WORDPRESS_VERSION=5.1",
                "WORDPRESS_SHA1=830eadf0afa15928d7f6856b1b85bf57b8e1f585"
            ],
            "Cmd": [
                "apache2-foreground"
            ],
            "ArgsEscaped": true,
            "Image": "sha256:0e68fcd954487398fcfc5b0b510a0c76deee2d7f547030f233d81064242d9962",
            "Volumes": {
                "/var/www/html": {}
            },
            "WorkingDir": "/var/www/html",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": null
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 420978171,
        "VirtualSize": 420978171,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/9a2074c31c8783cf0e36805602523f866d3ee1bec35780d0d46ee86c5207c3fa/diff:/var/lib/docker/overlay2/ad8f219792614c0609c5d8fb77a2863dbae1fe5c107fe0ad732ec5249de0e33b/diff:/var/lib/docker/overlay2/56a6e4719ef5af782cdc9a39022f6944dc83ba70d05f07c6bd39d4ed4dc5b84b/diff:/var/lib/docker/overlay2/6dc562d258b32c5b8442e4aad516dbf1a8bee70de3202b813405cf16bef8dd5b/diff:/var/lib/docker/overlay2/a0c558bae0dece848f96f3262895cc493ee2d023c55c15f9241ee77f60ac5fb3/diff:/var/lib/docker/overlay2/404b89feca0095472fad1b7e39d8f3f8a59c3f1fcb2a64beaf97bb298a1aea68/diff:/var/lib/docker/overlay2/eef71fe0291f3617dc44487210c8796c3b7cb7ee8ba7ea7ca91f18e01ce5b190/diff:/var/lib/docker/overlay2/32aa89432f2af18c60b39915cc020c7b38042d849bbebc4176775e6ce0500b34/diff:/var/lib/docker/overlay2/864d02a2fbed5050d2c5262d9388c6eca8fa9410aedb8f4965a78cc9cbbd26f0/diff:/var/lib/docker/overlay2/1492f7be80212e9fbeee94fa03ae9986ef67a56d1db5320cb2bcd39818098c26/diff:/var/lib/docker/overlay2/f602b93fff0d8203e6ce1b7347b71d1d1ed61be1d8e9ed0161d5960e8b688ea7/diff:/var/lib/docker/overlay2/ac63f6369af63872fbd058f377fbda791fd82e61cb454e63e08b6563a238a6d6/diff:/var/lib/docker/overlay2/336b997fb354fcc60d2852ffb307518c27310b739be4500748418ee03065b49d/diff:/var/lib/docker/overlay2/1face1154c9b920d7bf6e6301aef4d975f293b44a72e432fb90933eba088a980/diff:/var/lib/docker/overlay2/05a4cb901f966bc344bd888523948635a05fa32ac141a7003d518ee312e6e654/diff:/var/lib/docker/overlay2/6de9f5453867ea69ce904ae681707a162256e9ac0eac09ffd67a67ec994a7f55/diff:/var/lib/docker/overlay2/ab5579709ed2e02e9a4042bb0f47cc1443033943735a07de5271887c3129e3f8/diff",
                "MergedDir": "/var/lib/docker/overlay2/23d92dcc2e9d1bb315472632076e0fd1276af8fd15001b2afed2697040fdb5b8/merged",
                "UpperDir": "/var/lib/docker/overlay2/23d92dcc2e9d1bb315472632076e0fd1276af8fd15001b2afed2697040fdb5b8/diff",
                "WorkDir": "/var/lib/docker/overlay2/23d92dcc2e9d1bb315472632076e0fd1276af8fd15001b2afed2697040fdb5b8/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:6744ca1b11903f4db4d5e26145f6dd20f9a6d321a7f725f1a0a7a45a4174c579",
                "sha256:253661a0181f6e428d4b18044345c94f4a7a5ff2bfaac5e577233a5a0f6253ae",
                "sha256:a816c28953b8131ecfc688a893e587dfc8208bdaac77358bc6492bdd5dc0d348",
                "sha256:d03212c1c3b40f41a0ec9234c4a27d1ad5f4152535a7aefb64b594650b7c0ec1",
                "sha256:58fe0b297c5f05ff53fab5ddebd18e29be4612ff1d86e3ba36972d332eaa9226",
                "sha256:814c58278632ce6126d46dbcf94bbb82da95a028433c97f68e5d0bfb7334ad5f",
                "sha256:db1aa1e29454dd93a39f4a2430d821a2f8105a838e0829bdc11df08a9077fc41",
                "sha256:74cc7793dc7cad215b8c19dbcd4477817ab7fad45fd56b70053ea9e35117ba80",
                "sha256:eec38371288b862935aea32f99af2c53b1c5e1efef0430c0e1c61b8b430cc164",
                "sha256:4fb6ef75f6fe784233e93c492528afd28348f4305fc4171186695de7f11185ee",
                "sha256:6122d2ebfff55ca3c75c5bf4cca384f0429fc22eb918e85277ce24b27541e764",
                "sha256:09b8598177144510d1ba32f5076aa550e8147820622d6380d3e3d1f07332bb9a",
                "sha256:f5811741939ea5b1a9ac1daeb03ad749ede650bb94786cbd2e133b0929316a71",
                "sha256:db617e815ba343fa6a9c134ef95801334b58b98fd84f66c7e0ca4f953558d950",
                "sha256:006f1a7830fb6d5e18d8a985c59a2ab065bb5e4e8f79dcc675c9921e87a88465",
                "sha256:5c7aaf692e29c8495cd8c2aab354e5216bd36f4c739856ced099d8747f91e331",
                "sha256:0074dd8768386e10fce7a27829c8e65328fd80cc974f8594aa867ae0bf0471ff",
                "sha256:75ccfbf9c863e35df8df1d4a1c4179146d81bc1a45cba7d946570446dde592f4"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]
```
{% endtab %}
{% endtabs %}

## Help


#### Exercise n°1

Get the documentation of a specific field of a resource.

{% tabs %}
{% tab title="Command" %}
```bash
docker image --help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash

Usage:	docker image COMMAND

Manage images

Commands:
  build       Build an image from a Dockerfile
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Display detailed information on one or more images
  load        Load an image from a tar archive or STDIN
  ls          List images
  prune       Remove unused images
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rm          Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

Run 'docker image COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## Delete

The _delete_ command delete resources by filenames, stdin, resources and names, or by resources and label selector.

A Volume can only be deleted if it is not attached to a Pod. Use with caution, a deleted volumes cannot be recover.

Note that the delete command does NOT do resource version checks, so if someone submits an update to a resource right when you submit a delete, their update will be lost along with the rest of the resource.

#### Exercise n°1

Delete the previous volumes deployed in the default namespace.

```bash
# Delete an Image specific with is identifier
docker image rm 05e305efac8d

# Delete all unused images
docker image prune

# Delete all images
docker image prune -a
```

## Module exercise


## External documentation

Those documentations can help you to go further in this topic :

* Docker official documentation on [images](https://docs.docker.com/engine/reference/commandline/images/)
