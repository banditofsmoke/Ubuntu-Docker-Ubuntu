# Installing Docker on Ubuntu

This guide will walk you through the process of installing Docker on Ubuntu. Docker is a platform for developing, shipping, and running applications in containers.

## Prerequisites

- Ubuntu operating system (This guide was tested on Ubuntu 24.04 Noble Numbat)
- A user account with sudo privileges

## Installation Steps

1. Update your existing list of packages:

```bash
sudo apt update
```

2. Install prerequisite packages:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

3. Add Docker's official GPG key:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. Add the Docker repository to APT sources:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Update the package database with Docker packages from the newly added repo:

```bash
sudo apt update
```

6. Install Docker:

```bash
sudo apt install docker-ce docker-ce-cli containerd.io
```

7. Verify that Docker is installed correctly by running the hello-world image:

```bash
sudo docker run hello-world
```

## Post-installation Steps

To use Docker as a non-root user, you need to add your user to the docker group:

```bash
sudo usermod -aG docker $USER
```

Then, either log out and log back in, or run this command to activate the changes to groups:

```bash
newgrp docker
```

## Verify Installation

After completing the installation and post-installation steps, you can verify your Docker installation:

1. Check the Docker version:

```bash
docker --version
```

2. Run an Ubuntu container:

```bash
docker run -it ubuntu bash
```

This command will download an Ubuntu image if it's not already present, and start an interactive bash shell inside the container.

## Exploring Docker

Once inside the Ubuntu container, you can explore and run commands as if you were in a fresh Ubuntu system. Here are some things to try:

- View the Ubuntu version: `cat /etc/os-release`
- Update package lists: `apt update`
- Install a package: `apt install <package-name>`
- Create a file: `touch newfile.txt`

Remember, changes made inside the container are isolated from your host system. To exit the container, type `exit` or use Ctrl+D.

## Next Steps

- Explore Docker documentation to learn more about images, containers, and Docker Compose.
- Try running different containers and applications.
- Learn about building your own Docker images.

Happy Dockerizing!
