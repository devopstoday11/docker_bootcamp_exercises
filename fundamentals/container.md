# Container

## Module Overview

At the end of this module, you will :

* _Learn to run a container_
* _Learn to connect to a container_
* _Learn to manage a container_

## Help

Docker is an open source and popular operating system-level virtualization (commonly known as “containerization”) technology that runs on Linux, MacOS and Windows. Docker makes it easier to create, deploy, and run applications by using containers.

With containers, developers can package up an application with everything needed to run the application : the code, a run-time, libraries, environment variables, configuration files, and ship it all out as one package.

Docker provide an easy command to manage each object. The default format of the command is :

```bash
docker <object> <command> <arguments>
```

The Docker command line take some parameters :
* Object : The Docker object to manage (container, image, secret, service, etc).
* Command : A verb defining what to do on the object.
* Arguments : Some arguments depending on the action.

The recommended approach is to explicitly defined the object that you want to manage. In the case of container management, the recommended command is : docker container <command>

### Exercise n°1

Get the Docker container management help information from the Docker command line.

{% tabs %}
{% tab title="Command" %}
```bash
docker container help
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Usage:	docker container COMMAND

Manage containers

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  commit      Create a new image from a container\'s changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container\'s filesystem
  exec        Run a command in a running container
  export      Export a container\'s filesystem as a tar archive
  inspect     Display detailed information on one or more containers
  kill        Kill one or more running containers
  logs        Fetch the logs of a container
  ls          List containers
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  prune       Remove all stopped containers
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  run         Run a command in a new container
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker container COMMAND --help' for more information on a command.
```
{% endtab %}
{% endtabs %}

## Run



### Exercise n°1

Run a container based on the latest Ubuntu image and get the content of the /etc/hosts file.

{% tabs %}
{% tab title="Command" %}
```bash
docker container run ubuntu:latest cat /etc/hosts
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
898c46f3b1a1: Pull complete
63366dfa0a50: Pull complete
041d4cd74a92: Pull complete
6e1bee0f8701: Pull complete
Digest: sha256:017eef0b616011647b269b5c65826e2e2ebddbe5d1f8c1e56b3599fb14fabec8
Status: Downloaded newer image for ubuntu:latest
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
172.17.0.2	3cd7b8d3ef11
```
{% endtab %}
{% endtabs %}

### Exercise n°2

Run a container based on the latest Ubuntu image in detached mode.

{% tabs %}
{% tab title="Command" %}
```bash
docker container run -d ubuntu:latest cat /etc/hosts
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
9f17869ffa1e3f0c70c62142157424f14e5e684f532e05d7d377fab99b821810
```
{% endtab %}
{% endtabs %}

### Exercise n°3

Run a container based on the latest Ubuntu image and attach the current TTY session to the container. Run the same command : cat /etc/hosts

{% tabs %}
{% tab title="Command" %}
```bash
docker container run -d -i -t ubuntu:latest cat /etc/hosts
# or
docker container run -dit ubuntu:latest cat /etc/hosts
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
root@1d3eebce0ead:/# cat /etc/hosts
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
172.17.0.3	1d3eebce0ead
```
{% endtab %}
{% endtabs %}

#### Exercise n°4

Run a detached nginx container named _mythirdnginx_ based on the latest version and expose the port 80.

{% tabs %}
{% tab title="Command" %}
```bash
docker container run -d --name mythirdnginx --port 80:80 nginx
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
27833a3ba0a5: Pull complete 
ea005e36e544: Pull complete 
d172c7f0578d: Pull complete 
Digest: sha256:e71b1bf4281f25533cf15e6e5f9be4dac74d2328152edf7ecde23abc54e16c1c
Status: Downloaded newer image for nginx:latest
45addb2045a54c4eeac6f84e2c661befcb4b060bd03387d4657e47120ca33bb2
```
{% endtab %}
{% endtabs %}

Try to access the nginx default web page to ensure that the web server is up.

{% tabs %}
{% tab title="Command" %}
```bash
curl http://127.0.0.1
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```
{% endtab %}
{% endtabs %}

## Create


#### Exercise n°1

Create an nginx container named _mylatestnginx_ based on the latest version

{% tabs %}
{% tab title="Command" %}
```bash
docker container create --name mylatestnginx nginx
# or 
docker container create --name mylatestnginx nginx:latest
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
7e3cf55b762e53b309f4aa946837eb5320b4702edba916ce534e2e0c90914e2a
```
{% endtab %}
{% endtabs %}

{% hint style="info" %} Note that the latest nginx Docker image is not downloaded because it has already be done in the previous exercise. {% endhint %}

#### Exercise n°2

Create an nginx container named _myversionednginx_ based on the 1.13 version

{% tabs %}
{% tab title="Command" %}
```bash
docker container create --name myversionednginx nginx:1.13
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
Unable to find image 'nginx:1.13' locally
1.13: Pulling from library/nginx
f2aa67a397c4: Pull complete 
3c091c23e29d: Pull complete 
4a99993b8636: Pull complete 
Digest: sha256:b1d09e9718890e6ebbbd2bc319ef1611559e30ce1b6f56b2e3b479d9da51dc35
Status: Downloaded newer image for nginx:1.13
2454d55bb278d807eab2f50bd4b74bcf9946d95ff0e4a6e39f3bc7c93f718c30
```
{% endtab %}
{% endtabs %}

## Get

The _get_ command list the object asked. It could be a single object or a list of multiple objects comma separated. This command is useful to get the status of each object. The output can be formatted to only display some information based on some json search or external tools like `tr`, `sort`, `uniq`.

The default output display some useful information about each services :

* Container ID : the unique identifier of the Docker container
* Image : the Docker image used to run the container
* Command : the init command of the Docker container
* Created :  the age of the object since his creation
* Status : the status of the container
* Ports : a list of ports opened
* Names : the object name

#### Exercise n°1

List all running Containers.

{% tabs %}
{% tab title="Command" %}
```bash
docker container ls
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
45addb2045a5        nginx               "nginx -g 'daemon of…"   1 minutes ago       Up 8 minutes        0.0.0.0:80->80/tcp   mythirdnginx
30246db7d87c        ubuntu:latest       "/bin/bash"              4 minutes ago       Up About an hour                         nervous_ellis
```
{% endtab %}
{% endtabs %}

#### Exercise n°2

List all existing Containers.

{% tabs %}
{% tab title="Command" %}
```bash
docker container ls -a
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
45addb2045a5        nginx               "nginx -g 'daemon of…"   1 minutes ago       Up 5 minutes        0.0.0.0:80->80/tcp   mythirdnginx
2454d55bb278        nginx:1.13          "nginx -g 'daemon of…"   2 minutes ago       Created                                  myversionednginx
7e3cf55b762e        nginx               "nginx -g 'daemon of…"   3 minutes ago       Created                                  peaceful_kowalevski
30246db7d87c        ubuntu:latest       "/bin/bash"              4 minutes ago       Up About an hour                         nervous_ellis
                                 nervous_ellis
2cc7b7c2f836        ubuntu:latest       "cat /etc/hosts"         5 minutes ago       Exited (0) 4 minutes ago                       angry_borg
90f245510b69        ubuntu:latest       "cat /etc/hosts"         6 minutes ago       Exited (0) 4 minutes ago                       elastic_perlman
c83a99c41de2        ubuntu:latest       "cat /etc/hosts"         7 minutes ago       Exited (0) 5 minutes ago                       stoic_torvalds
```
{% endtab %}
{% endtabs %}

## Inspect

Once an object is running, it is inevitably a need to debug problems or check the configuration deployed.

The _inspect_ command display a lot of configuration information about the Images \(labels, tags, name, Id, etc.\).

This command is really useful to introspect and debug an object deployed in a cluster.

#### Exercise  n°1

Inspect one of the existing Container.

{% tabs %}
{% tab title="Command" %}
```bash
docker container inspect 05e305efac8d
```
{% endtab %}

{% tab title="CLI Return" %}
```text
[
    {
        "Id": "30246db7d87c22a09c34259ca32694302446e7a9ce98fcc69ef2761322cc9d14",
        "Created": "2019-04-26T01:47:50.692018592Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 11331,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2019-04-26T01:47:51.301021756Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:94e814e2efa8845d95b2112d54497fbad173e45121ce9255b93401392f538499",
        "ResolvConfPath": "/var/lib/docker/containers/30246db7d87c22a09c34259ca32694302446e7a9ce98fcc69ef2761322cc9d14/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/30246db7d87c22a09c34259ca32694302446e7a9ce98fcc69ef2761322cc9d14/hostname",
        "HostsPath": "/var/lib/docker/containers/30246db7d87c22a09c34259ca32694302446e7a9ce98fcc69ef2761322cc9d14/hosts",
        "LogPath": "/var/lib/docker/containers/30246db7d87c22a09c34259ca32694302446e7a9ce98fcc69ef2761322cc9d14/30246db7d87c22a09c34259ca32694302446e7a9ce98fcc69ef2761322cc9d14-json.log",
        "Name": "/nervous_ellis",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "docker-default",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "shareable",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DiskQuota": 0,
            "KernelMemory": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": 0,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/c7ecf535a012b476dd6ef7631e207def93360115eb0688de692d5509eee7bf55-init/diff:/var/lib/docker/overlay2/9765e4a518ce215b31a70b5230f2cacef4e865f7cb53a5d408d4116256aa28ff/diff:/var/lib/docker/overlay2/a652c59716d1fc67d17bdf4d6e818b978b3eb15110d0bc63cbbfa37e0f4ff6a1/diff:/var/lib/docker/overlay2/a8f5370cd81afa57980a2d0d80567a05035304f54cd940e60a02dba5c6584b03/diff:/var/lib/docker/overlay2/0194832e4566fc07b8ea82b20638efd20b2f4374c49de04f389d758bdb1190e8/diff",
                "MergedDir": "/var/lib/docker/overlay2/c7ecf535a012b476dd6ef7631e207def93360115eb0688de692d5509eee7bf55/merged",
                "UpperDir": "/var/lib/docker/overlay2/c7ecf535a012b476dd6ef7631e207def93360115eb0688de692d5509eee7bf55/diff",
                "WorkDir": "/var/lib/docker/overlay2/c7ecf535a012b476dd6ef7631e207def93360115eb0688de692d5509eee7bf55/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "30246db7d87c",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "ArgsEscaped": true,
            "Image": "ubuntu:latest",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "034cc618d0e43208a763d2c34f8b5d569b1259af54b4d29dc0268ae5911b14ef",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "/var/run/docker/netns/034cc618d0e4",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "7b065e0acfee35a159cd89017bc4342bd272ce62a030bb8c95da6aa338e00076",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "b1c3e7c04e1fd7f73e93f0e14ad29be8d9a9fbcf2e141c3372c38825fb2d1463",
                    "EndpointID": "7b065e0acfee35a159cd89017bc4342bd272ce62a030bb8c95da6aa338e00076",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]
```
{% endtab %}
{% endtabs %}

## Logs


#### Exercise n°1

Get the logs of an existing container based on his identifier.

{% tabs %}
{% tab title="Command" %}
```bash
docker container logs 2cc7b7c2f836
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
172.17.0.2	2cc7b7c2f836
```
{% endtab %}
{% endtabs %}

#### Exercise n°2

Get the logs of an existing container based on his name.

{% tabs %}
{% tab title="Command" %}
```bash
docker container logs angry_borg
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
172.17.0.2	2cc7b7c2f836
```
{% endtab %}
{% endtabs %}

## Start / Stop

## Exec


#### Exercise n°1

Connect to an existing container based on his identifier.

{% tabs %}
{% tab title="Command" %}
```bash
docker container exec -it 30246db7d87c sh
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
$
$ exit
```
{% endtab %}
{% endtabs %}

#### Exercise n°2

Connect to an existing container based on his name.

{% tabs %}
{% tab title="Command" %}
```bash
docker container exec -it nervous_ellis sh
```
{% endtab %}

{% tab title="CLI Return" %}
```bash
$
$ exit
```
{% endtab %}
{% endtabs %}

## Delete

The _delete_ command delete resources by filenames, stdin, resources and names, or by resources and label selector.

A container can only be deleted if it is stopped. An error message will be displayed if the container cannot be deleted.

Note that the delete command does NOT do resource version checks, so if someone submits an update to a resource right when you submit a delete, their update will be lost along with the rest of the resource.

#### Exercise n°1

Delete the previous volumes deployed in the default namespace.

```bash
# Delete an Image specific with his identifier
docker container rm 30246db7d87c

# Delete an Image specific with his name
docker container rm mythirdnginx

# Delete all unused containers
docker container prune
```

## Module exercise


## External documentation

Those documentations can help you to go further in this topic :

* Docker official documentation on [container](https://www.docker.com/resources/what-container)
* Docker official documentation on [docker container command](https://docs.docker.com/engine/reference/commandline/container/)
