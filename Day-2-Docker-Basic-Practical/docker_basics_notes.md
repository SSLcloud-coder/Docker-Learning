
# 🐳 Docker Basics Notes (from Red Hat DO276 Guide)

## **1. Docker Overview**
Docker is a containerization platform that packages applications and dependencies into portable containers.

### **Core Components**
| Term | Description |
|------|--------------|
| **Image** | Read-only template used to create containers. |
| **Container** | Running instance of an image, isolated environment. |
| **Registry** | Repository for storing and distributing images (Docker Hub, Red Hat Registry). |
| **Tag** | Version label for an image, e.g., `mysql:5.5` or `mysql:latest`. |

---

## **2. Docker Images**
- Images are **immutable** and built from multiple **layers**.  
- Each layer represents a step in a **Dockerfile**.  
- Identified by:  
  ```
  [registry_uri/][user_name/]image_name[:tag]
  ```
  Example: `docker.io/mysql:latest`

### **Common Image Commands**
```bash
docker images               # List all local images
docker pull mysql:5.5       # Download image from registry
docker rmi mysql:latest     # Remove image
docker save -o mysql.tar mysql:5.5   # Save image to a file
docker load -i mysql.tar             # Load image from file
```

---

## **3. Containers**
- Containers are isolated environments created from images.  
- Use **namespaces**, **cgroups**, and **SELinux** for isolation and control.

### **Container Commands**
```bash
docker run --name mysql-container mysql:5.5
docker run -d mysql:5.5                    # Run in detached mode
docker exec -it mysql-container /bin/bash  # Access container shell
docker stop mysql-container
docker rm mysql-container
```

---

## **4. Types of Docker Images**
| Image Type | Description |
|-------------|--------------|
| **Base Image** | Built from scratch (e.g., `rhel7`, `ubuntu`). |
| **Parent Image** | Used as foundation for custom images. |
| **Child Image** | Extends parent image with additional layers. |
| **Custom Image** | User-created via Dockerfile or `docker commit`. |

---

## **5. Building Custom Images (Dockerfile)**
Example Dockerfile:
```Dockerfile
FROM rhel7.2
MAINTAINER Your Name <email>
LABEL description="Basic Apache container"
RUN yum -y install httpd && yum clean all
EXPOSE 80
CMD ["httpd", "-D", "FOREGROUND"]
```

Build the image:
```bash
docker build -t do276/apache .
```

---

## **6. Export vs Save**
| Command | Purpose | Keeps Metadata |
|----------|----------|----------------|
| `docker save` / `docker load` | Backup & restore full image | ✅ Yes |
| `docker export` / `docker import` | Save container filesystem only | ❌ No |

---

## **7. Tagging and Sharing Images**
```bash
docker tag do276/custom-httpd:v1.0 workstation.lab.example.com:5000/do276/custom-httpd:v1.0
docker push workstation.lab.example.com:5000/do276/custom-httpd:v1.0
```

---

> ✨ *Notes derived from Red Hat DO276 (Containerizing Software Applications v7.2)*
