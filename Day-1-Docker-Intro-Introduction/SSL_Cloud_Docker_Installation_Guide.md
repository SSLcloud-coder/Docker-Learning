# 🐳 Docker Installation Guide on CentOS / RHEL  
**SSL Cloud – Docker Practical Setup**

---

## 🔹 Step 1: Add the Official Docker Repository

```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

✅ **Explanation:**  
This command adds the official Docker repository to your system so that Docker packages can be installed directly from Docker’s maintained source.

---

## 🔹 Step 2: Install Docker Engine and Required Components

```bash
sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

✅ **Explanation:**
- **docker-ce** → Main Docker Engine (Community Edition)  
- **docker-ce-cli** → Command Line Interface for Docker  
- **containerd.io** → Container runtime used by Docker  
- **docker-buildx-plugin** → Advanced image builder tool  
- **docker-compose-plugin** → Used to run multi-container applications

---

## 🔹 Step 3: Start and Enable containerd Service

```bash
sudo systemctl daemon-reload
sudo systemctl start containerd
sudo systemctl enable containerd
```

✅ **Explanation:**  
Containerd is a core container runtime used by Docker.  
- **daemon-reload** → Reload system services  
- **start** → Start the service immediately  
- **enable** → Start the service automatically on boot

---

## 🔹 Step 4: Start and Enable Docker Service

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

✅ **Explanation:**  
This starts the Docker daemon and ensures it runs automatically at every system startup.

---

## 🔹 Step 5: Verify Docker Installation

```bash
docker --version
docker compose version
```

✅ **Output Example:**
```
Docker version 27.0.3, build 12345
Docker Compose version v2.29.1
```

---

## 🔹 Step 6: Test Docker Installation

```bash
sudo docker run hello-world
```

✅ **Explanation:**  
- This pulls the official **hello-world** image from Docker Hub.  
- If Docker is installed correctly, you’ll see a success message:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

---

## 🧠 Quick Verification Commands

| Purpose | Command |
|----------|----------|
| Check Docker service status | `systemctl status docker` |
| List Docker images | `docker images` |
| List running containers | `docker ps` |
| Show Docker info | `docker info` |

---

## 🎯 Conclusion

You’ve successfully installed and configured **Docker** on your **CentOS/RHEL** system.  
Now you’re ready to create, run, and manage containers like a pro! 🚀  

---

**© SSL Cloud | DevOps & Cloud Training**
