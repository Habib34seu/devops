# What is Docker?
Docker is a **containerization platform that provides a complete system for building and running software containers**. Containers package applications and their dependencies as ephemeral units that behave similarly to virtual machines, but share your host’s operating system kernel. **Containers ensure that our application works in any environment like development, test, or production.**

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
$ sudo docker version
```

```bash
abib@habib-VirtualBox:~$ sudo docker version
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


