# What is Docker?
Docker is a **containerization platform that provides a complete system for building and running software containers**. Containers package applications and their dependencies as ephemeral units that behave similarly to virtual machines, but share your host’s operating system kernel. **Containers ensure that our application works in any environment like development, test, or production.**

Some popular containerization tools include 
- Docker 
- Kubernetes
- Amazon Elastic Container Service(ECS)
- Docker Swarm
- Openshift
- podman (Res Hat Linux)

![Reference Image](/Docker/screenshort/docker_vm.png)

# Docker Engine 
1. Docker Daemon (dockerd)
    - Runs in the background and listens for Docker API requests.
    - Manages images, containers, networks, and storage volumes.
    - Handles container lifecycle (start, stop, restart, etc.).
2. Docker API 
    - Provides a RESTful interface for interacting with Docker Engine.
    - Used by the CLI and other applications to communicate with the daemon.
3. Docker CLI (docker)
    - A command-line tool that allows users to interact with Docker Engine.
    - Used for building images, managing containers, networks, and volumes.

![Reference Image](/Docker/screenshort/docker_engine.png)

## Docker Architecture

Docker uses a client-server architecture. **The Docker client talks to the Docker daemon**, which does the heavy lifting of building, running, and distributing your Docker containers. **The Docker client and daemon can run on the same system**, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface.

![Reference Image](/Docker/screenshort/docker_architecture.gif)


## How to install docker linux?

#### First Check Firewall limitations, OS requirements

```bash
habib@habib-VirtualBox:~$ cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=24.04
DISTRIB_CODENAME=noble
DISTRIB_DESCRIPTION="Ubuntu 24.04.1 LTS"
PRETTY_NAME="Ubuntu 24.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.1 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

```

#### Uninstall old versions
The unofficial packages to uninstall are:
- docker.io
- docker-compose
- docker-compose-v2
- docker-doc
- podman-docker
```bash
$ for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

#### Install using the convenience script

```bash
 $ curl -fsSL https://get.docker.com -o get-docker.sh
 $ sudo sh ./get-docker.sh --dry-run
```
#### Now Check docker version

```bash
$ docker --version
```
```bash
habib@habib-VirtualBox:~$ sudo docker version
Client: Docker Engine - Community
 Version:           27.5.1
 API version:       1.47
 Go version:        go1.22.11
 Git commit:        9f9e405
 Built:             Wed Jan 22 13:41:48 2025
 OS/Arch:           linux/amd64
 Context:           default

Server: Docker Engine - Community
 Engine:
  Version:          27.5.1
  API version:      1.47 (minimum version 1.24)
  Go version:       go1.22.11
  Git commit:       4c9b3b0
  Built:            Wed Jan 22 13:41:48 2025
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.7.25
  GitCommit:        bcc810d6b9066471b0b6fa75f557a15a1cbf31bb
 runc:
  Version:          1.2.4
  GitCommit:        v1.2.4-0-g6c52b3f
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

```
#### If we know how many images and containers are on my server we used this command
```bash
$ docker info
```

# Docker commands

### Docker pull 

docker pull is a command used in Docker to download a Docker image from a remote registry (such as Docker Hub) to your local machine.

```bash
docker pull <image_name>:<tag>
```
```bash
docker pull nginx
```
or
```bash
docker pull nginx: stable-alpine3.20-perl
```
### Run - start a container
The docker run command is used to run a container from an image.

```bash
docker run nginx
```
or 
- add custom name image
```bash
docker run  --name app1 nginx
```
or 
- add -d (-d mean run background)
```bash
docker run  -d --name app1 nginx
```
## Docker ps - list containers 
docker ps is a command used in Docker to list running containers.
```bash
docker ps [OPTIONS]
```
1. List only running containers:
```bash
docker ps 
```
```bash
CONTAINER ID   IMAGE     COMMAND                  CREATED       STATUS       PORTS     NAMES
793ca6cfa57c   nginx     "/docker-entrypoint.…"   2 hours ago   Up 2 hours   80/tcp    hardcore_thompson
```
2.List all containers (including stopped ones):

```bash
docker ps -a
```
```bash
CONTAINER ID   IMAGE     COMMAND                  CREATED       STATUS       PORTS     NAMES
793ca6cfa57c   nginx     "/docker-entrypoint.…"   2 hours ago   Up 2 hours   80/tcp    hardcore_thompson
```
3. Show only container IDs: 

```bash
docker ps -q
```

4. Filter containers by status (e.g., exited):

```bash
docker ps -a -f "status=exited"
```

5. Custom output format (show only names and status):

```bash
docker ps --format "table {{.Names}}\t{{.Status}}"
```
```bash
NAMES               STATUS
hardcore_thompson   Up 2 hours
```

## Docker stop

1. First check lists all running container

```bash
docker ps -a
```
```bash
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
d618b53c4ea2   nginx     "/docker-entrypoint.…"   24 seconds ago   Up 24 seconds   80/tcp    app1
793ca6cfa57c   nginx     "/docker-entrypoint.…"   2 hours ago      Up 2 hours      80/tcp    hardcore_thompson
```
2. Stop container

stop container id

```bash
docker stop d618b53c4ea2
```
or container name 
```bash
docker stop hardcore_thompson
```
## Force Stop a Container:
```bash
docker kill <container_id>
```
```bash
docker kill 793ca6cfa57c
```
## Docker container start

```bash
docker container start <container_id> [<container_id2> ...]
```

or 

```bash
docker start <container_id> [<container_id2> ...]
```

```bash
docker start 793ca6cfa57c
```
Now we check running docker container

```bash
docker ps -a
```
```bash
d618b53c4ea2   nginx     "/docker-entrypoint.…"   2 hours ago   Up 2 hours      80/tcp    app1
793ca6cfa57c   nginx     "/docker-entrypoint.…"   4 hours ago   Up 16 seconds   80/tcp    hardcore_thompson
```

## Start all stopped containers:

```bash
docker start $(docker ps -a -q)
```
- docker ps -a -q lists all stopped container IDs.
- The docker start command starts them one by one.

## Start a container and attach to its logs (interactive mode):

```bash
docker start -a my_container
```
or 

```bash
docker start -a 793ca6cfa57c
```
## How to show images

```bash
docker images
```
```bash
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    97662d24417b   6 days ago    192MB
ubuntu       latest    a04dc4851cbc   2 weeks ago   78.1MB
```
## What is ENTRYPOINT in Docker?
The ENTRYPOINT in Docker is a directive used in a Dockerfile to define the default executable (command) that runs when a container starts.

## Key Points:
- It specifies the main process that should run inside the container.
- Unlike CMD, ENTRYPOINT cannot be overridden by command-line arguments unless explicitly modified.
- It is commonly used when you want the container to behave like an executable program.
## Docker Inspect command :
The docker inspect command is used to retrieve detailed information about a Docker 
**container, image, network, or volume in JSON format**. <br />

It provides low-level system details such as 
- container configuration, 
- network settings, 
- mount points, 
- and runtime information.


```bash
docker inspect <object_id_or_name>
```

#### Inspect a Running or Stopped Container:

```bash
docker inspect my_container
```
or 

```bash
docker inspect 123456789abc
```

#### Inspect a Docker Image:

```bash
docker images
```
```bash
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    97662d24417b   7 days ago    192MB
ubuntu       latest    a04dc4851cbc   2 weeks ago   78.1MB
alpine       latest    b0c9d60fc5e3   5 weeks ago   7.83MB
```
```bash
docker inspect ubuntu
```

#### Get Specific Information (Using --format):

```bash
docker inspect -f '{{ .NetworkSettings.IPAddress }}' my_container
```
#### Get the container's ID:
```bash
docker inspect -f '{{ .Id }}' my_container
```
#### Check the container's status:

```bash
docker inspect -f '{{ .State.Status }}' my_container
```

#### Key Information Retrieved:
- Container: ID, Image, Command, Created Time, Status, Environment Variables, Mounts, Network Settings, etc.
- Image: ID, Parent ID, RepoTags, Size, Architecture, etc.
- Network: Name, ID, Subnet, Gateway, Connected Containers, etc.
- Volume: Name, Mount Path, Scope, etc.

#### Use Case Scenarios:
- Checking the IP address of a running container.
- Finding the mount path of a volume.
- Debugging network issues in Docker.
- Retrieving environment variables or labels of a container.
- Validating the image configuration before running a container.




























