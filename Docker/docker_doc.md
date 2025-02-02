# What is Docker?
Docker is a **containerization platform that provides a complete system for building and running software containers**. Containers package applications and their dependencies as ephemeral units that behave similarly to virtual machines, but share your host’s operating system kernel. **Containers ensure that our application works in any environment like development, test, or production.**

# Docker Architecture
Docker uses a **client-server driven architecture**.

#### Docker Engine
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



