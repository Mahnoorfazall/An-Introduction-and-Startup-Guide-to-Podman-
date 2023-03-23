# An Introduction and Startup Guide to Podman

![image](https://user-images.githubusercontent.com/117302353/227386920-2006a42d-f2fc-4877-99d8-662289120954.png)

Podman is a container engine that provides a powerful alternative to Docker. It is a tool for management of containers and images on Linux systems, designed to be simple, lightweight and secure.

# Podman vs. Docker

Podman and Docker are both container engines and share similarities but they also have several key differences.

## 1. Architecture
One of the main differences between Podman and Docker is their architecture. Docker runs as a client-server architecture, where a Docker daemon runs in the background and manages all the containers. Podman, on the other hand, runs as a standalone binary and does not require a daemon to be running in the background.

## 2. Security
Security is another area where Podman and Docker differ. Podman is designed with security in mind and has a more fine-grained approach to container security. By default, containers run as the user’s UID and GID, which provides an extra layer of security by preventing containers from running as the root user. Podman also supports SELinux, AppArmor, and seccomp, which can be used to further enhance container security. Docker, on the other hand, runs containers as the root user by default, which can pose a security risk.

## 3. Image Management
Both Podman and Docker support the use of container images, but they differ in their approach to image management. Docker relies on a centralized image registry, Docker Hub. Podman, on the other hand, supports multiple container image registries, including Docker Hub, Quay.io, and the Red Hat Container Registry.

## 4. Compatibility
Both Podman and Docker are compatible with the Open Container Initiative (OCI) specification, which means that they can run containers created by other OCI-compliant tools such as Kubernetes. However, Docker has a larger user base, which means that it has a wider range of tools and integrations available.

## 5. CLI
Podman and Docker also differ in their command-line interface (CLI). Podman has a simpler and more intuitive CLI, which can be easier for beginners to learn and use. Docker, on the other hand, has a more complex CLI with more advanced features and options.

# Installing Podman
To install Podman on Ubuntu follow these steps.
## 1. Add the Podman repository
`sudo add-apt-repository ppa:projectatomic/ppa`
## 2. Update the package manager
`sudo apt-get update`
## 3. Install Podman
`sudo apt-get install podman`
## 4. Verify Podman Installation
`podman --version`

# Creating an Image on Podman
Creating an image on Podman involves several steps. Here is a step-by-step guide to creating an image on Podman:

## 1. Create a Dockerfile
The first step is to create a Dockerfile that defines the image. 
`FROM ubuntu:latest`
`RUN apt-get update && apt-get install -y nginx`
`CMD ["nginx", "-g" "daemon off;"]`
 
These instructions in a Dockerfile create an image on latest version of Ubuntu and installs the Nginx web server.

## 2. Build the Image
Once you have created the Dockerfile, you can build the image using the following command. 
`podman build -t mynginx . `

## 3. Verify the image
After the image is built, you can verify that it was created successfully by running the following command:
`podman images`

## 4. Run the Container
You can run the container from the image using the following command
`podman run -d -p 80:80 mynginx`

# Podman Commands
Here are some of the basic commands of Podman
## podman run
Run a container from an image `podman run -it ubuntu:latest`
## podman ps
List all running containers `podman ps`
## podman images
List all the local images `podman images`
## podman pull
Download an image from a registry (Dockerhub) 
`podman pull centos:latest`
## podman stop
Stop a running container `podman stop container1`
## podman rm
Delete a container `podman rm container1`
## podman rmi
Delete an imagepodman `rmi image1`

# Conclusion
In conclusion, while Podman is a powerful container engine that can manage containers and images. If you prioritize security and simplicity, then Podman may be a better choice than tools like Docker. It is simple to set-up and start using as a new developer!
