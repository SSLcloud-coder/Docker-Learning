
# 🐳 Docker & Linux Command Reference (Extracted from Docker-Log)

This document provides detailed explanations for every command found in the uploaded PuTTY session log from the Docker host system.

---

## 🧭 1. Basic Linux & System Commands

| Command | Description | Example |
|----------|--------------|----------|
| `date` | Displays the current system date and time. | `date` |
| `df -HT` | Shows disk space usage in human-readable format. | `df -HT /` |
| `ls` | Lists files and directories. | `ls /var/lib/docker/` |
| `ls -ld /var/lib/docker/` | Shows directory details including permissions. | `ls -ld /var/lib/docker/` |
| `cat /etc/os-release` | Displays OS info (version, ID, etc.). | `cat /etc/os-release` |
| `ping <IP>` | Tests network connectivity. | `ping 172.17.0.2` |
| `systemctl enable --now cockpit.socket` | Enables and starts Cockpit web console. | `systemctl enable --now cockpit.socket` |

---

## 🐳 2. Docker Basic Commands

| Command | Description | Example |
|----------|--------------|----------|
| `docker images` | Lists local Docker images. | `docker images` |
| `docker ps` | Lists running containers. | `docker ps` |
| `docker ps -a` | Lists all containers. | `docker ps -a` |
| `docker pull <image>` | Downloads an image from Docker Hub. | `docker pull nginx` |
| `docker info` | Shows detailed system information. | `docker info | grep -i root` |
| `docker system df` | Displays disk space used by Docker. | `docker system df` |

---

## ⚙️ 3. Container Management

| Command | Description | Example |
|----------|--------------|----------|
| `docker run -d --name=<name> <image>` | Creates and runs a container in detached mode. | `docker run -d --name=web1 nginx` |
| `docker run -it --name=<name> <image>` | Runs a container interactively. | `docker run -it --name=con1 ubuntu` |
| `docker start <container>` | Starts a stopped container. | `docker start web1` |
| `docker stop <container>` | Stops a running container. | `docker stop web1` |
| `docker rm <container>` | Removes a stopped container. | `docker rm web1` |
| `docker rm $(docker ps -a -q)` | Removes all stopped containers. | Bulk cleanup |
| `docker exec -it <container> <cmd>` | Runs a command inside a running container. | `docker exec -it web1 /bin/bash` |
| `docker attach <container>` | Attaches to a running container’s console. | `docker attach raw1` |
| `docker top <container>` | Displays running processes inside a container. | `docker top web1` |
| `docker stats <container>` | Shows live resource usage. | `docker stats web1` |

---

## 🧩 4. Image Management

| Command | Description | Example |
|----------|--------------|----------|
| `docker rmi <image>` | Removes a Docker image. | `docker rmi nginx` |
| `docker rmi -f $(docker images -a -q)` | Force removes all images. | Cleanup all |
| `docker history <image>` | Displays image layer history. | `docker history httpd:latest` |
| `docker inspect <image/container>` | Shows detailed configuration (JSON). | `docker inspect httpd` |
| `docker inspect <container> | grep -i ipaddress` | Extracts container IP info. | `docker inspect web1 | grep -i ipaddress` |

---

## 🪪 5. Docker Networking & Debugging

| Command | Description | Example |
|----------|--------------|----------|
| `docker inspect <container> | grep -i memory` | Checks container memory info. | `docker inspect db1 | grep -i memory` |
| `docker inspect <container> | grep -i cpu` | Checks CPU allocation. | `docker inspect LB3 | grep -i cpu` |
| `docker logs <container>` | Shows container logs. | `docker logs db1` |

---

## 🧱 6. External Container Tools

| Tool | Command | Description |
|------|----------|-------------|
| **Podman** | `podman search registry.redhat.io/nginx` | Searches images on Red Hat registry. |
| **Skopeo** | `skopeo inspect docker://docker.io/httpd` | Checks remote image metadata without pulling. |
| **YUM** | `yum install skopeo -y` | Installs `skopeo` utility. |

---

## 🧹 7. Bulk & Automation Commands

| Command | Description | Example |
|----------|--------------|----------|
| `docker stop $(docker ps -q)` | Stops all running containers. | Bulk stop |
| `docker rm $(docker ps -a -q)` | Removes all stopped containers. | Bulk remove |
| `docker rmi -f $(docker images -a -q)` | Deletes all Docker images. | Cleanup |
| `docker system prune` | Cleans up unused resources. | Safe cleanup |

---

## 🧠 8. Docker Application Examples

| Example | Description |
|----------|-------------|
| `docker run -d --name=db1 -e MYSQL_ROOT_PASSWORD=redhat mysql` | Runs MySQL container with root password. |
| `docker run -d --name=web1 nginx` | Runs Nginx web server container. |
| `docker run -d --name=server1 nginx` | Another Nginx example. |
| `docker run -d --name=LB1 httpd` | Apache load balancer simulation. |
| `docker exec -it server1 /bin/bash` | Opens shell inside container. |

---


