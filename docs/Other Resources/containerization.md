## Overview of containers
Containers are lightweight, portable, and self-sufficient units that package an application and its dependencies together. They provide a consistent environment for applications to run, regardless of the underlying infrastructure. Containers are isolated from each other and the host system, which allows for better resource utilization and easier management.
## Container orchestrators
There are several container orchestrators available, each with its own features and capabilities. Some of the most popular ones include:

- **Docker**: The most widely used container platform, which allows developers to easily create, deploy, and manage containers.
- **Podman**: A newer, daemonless container engine that allows users to manage containers without requiring a central service or root privileges. Podman is compatible with Docker commands, making it easy to switch between the two.
- **Kubernetes**: An open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications.
- **OpenShift**: A Kubernetes-based platform that provides additional features for managing containerized applications, such as developer tools and a web console.
## Getting started with containerization
To get started with containerization, you need to install a container orchestrator on your system. The most common choice is Docker, which can be installed on various operating systems. Follow the [official Docker installation guide](https://docs.docker.com/get-docker/) to set up Docker on your machine.
Once Docker is installed, you can start creating and managing containers. Here are some basic commands to help you get started:
#### Pull an image from Docker Hub
```bash
docker pull hello-world
```
#### Run a container from the pulled image
```bash
docker run hello-world
```
You can also create your own Docker images by writing a `Dockerfile`, which contains instructions for building the image. For example, a simple `Dockerfile` might look like this:
```dockerfile title="Dockerfile"
FROM alpine:latest
CMD ["echo", "Hello, World!"]
```
To build the image from the `Dockerfile`, run the following command in the same directory as the `Dockerfile`:
```bash
docker build -t hello .
```
After building the image, you can run it as a container:
```bash
docker run hello
```
## Resources
- [Docker Documentation](https://docs.docker.com/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Podman Documentation](https://podman.io/get-started)
- [OpenShift Documentation](https://docs.redhat.com/en/documentation/openshift_container_platform)
