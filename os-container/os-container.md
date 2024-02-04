# Podman Notes!

### Introduction to Running Ubuntu as a podman Container inside podman.

Explore the efficient deployment of Ubuntu as a podman container, a lightweight alternative to traditional virtual machines. podman, a widely acclaimed programming tool, has significantly streamlined the process of application deployment through containerization.

**Author:** Anubhav Gain
**Reading Time:** 11–14 minutes
**You can use it without non sudo**

## Table of Contents

1. [Getting Started](#getting-started)

   1. [Step 1: Obtaining the Ubuntu podman Image](#step-1-obtaining-the-ubuntu-podman-image)
   2. [Step 2: Running the Ubuntu podman Image](#step-2-running-the-ubuntu-podman-image)

2. [Working with Ubuntu in podman](#working-with-ubuntu-in-podman)
   1. [Executing Linux Commands](#executing-linux-commands)
   2. [Preserving the podman Container State](#preserving-the-podman-container-state)
   3. [Persisting Data on the Ubuntu podman Container](#persisting-data-on-the-ubuntu-podman-container)

## Getting Started

### Step 1: Obtaining the Ubuntu podman Image

If podman is not installed, please refer to our [guide on installing podman on Ubuntu](#). podman Hub is the recommended repository for official podman images. Download the latest Ubuntu podman image:

```bash
sudo podman pull ubuntu
```

For a specific version:

```bash
sudo podman pull ubuntu:20.04
```

List all podman images:

```bash
sudo podman images
```

### Step 2: Running the Ubuntu podman Image

Run the downloaded image in interactive terminal mode:

```bash
sudo podman run -ti --rm ubuntu /bin/bash
```

Explore the lightweight Ubuntu container, devoid of a graphical user interface (GUI) and unnecessary tools.
This command tells podman to run the podman Ubuntu container in an interactive terminal mode (-ti). The /bin/bash argument is a way of telling the container to run the Bash shell terminal. Finally, the --rm flag instructs podman to automatically remove the Ubuntu podman container after we stop it.

## Working with Ubuntu in podman

### Executing Linux Commands

Execute Linux commands inside the Ubuntu podman container. For example:

```bash
cat /etc/os-release
```

Install additional packages as needed:

```bash
apt update && apt install lsb-core
```

### Preserving the podman Container State

Save changes made to the container:

```bash
sudo podman ps
sudo podman commit -p container_id myubuntu
```

Create a custom podman image named "myubuntu" with the changes.

### Persisting Data on the Ubuntu podman Container

Utilize podman's data persistence features:

```bash
sudo mkdir -p podman_Share
sudo podman stop container_id
sudo podman run -ti --rm -v ~/podman_Share:/data ubuntu /bin/bash
```

Access and modify files in the `/data` directory, persisting data between host and container.

# Persisting Data on the Ubuntu podman Container

One powerful feature of podman is the ability to persist or share data with the host machine. There are two main options for persisting data:

- Mounted volumes
- podman volumes

podman recommends using podman volumes over mounted volumes.

## Creating a podman Volume

You can create a podman volume anywhere on your host machine. Let's create one in the home directory called `podman_Share`:

```
$ sudo mkdir ./podman_Share
```

## Stopping the Container

Next, stop the Ubuntu container using the following command. Substitute `container_id` with the actual ID of your Ubuntu podman container:

```
$ sudo podman stop container_id
```

## Running the Container with the Volume

Finally, we can run the Ubuntu podman image and mount the `podman_Share` directory as a volume using this command:

```
$ sudo podman run -ti --rm -v ./podman_Share:/data ubuntu /bin/bash
```

Alternatively, you can use a podman-compose file to easily start your containers with mounted volumes.

This will start the Ubuntu image and create the `/data` directory within the container. The `/data` directory is mapped to the `podman_Share` folder we created earlier.

Any files created or modified in `/data` will now also be accessible in `podman_Share` on the host, and vice versa.

## Summary

The key points are:

- podman volumes allow persisting data between the host and container
- Create a podman volume on the host machine
- Mount it when starting the container using `-v host_dir:container_dir`
- Modifications on either the host or container will be mirrored

## Conclusion

podman provides a powerful and efficient alternative to virtual machines. Deploying a lightweight Ubuntu podman container allows for secure application deployment and management. Experiment with podman to unlock its diverse capabilities.
