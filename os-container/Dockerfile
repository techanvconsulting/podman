# Use the official Ubuntu base image
FROM ubuntu

# Author information
LABEL author="Anubhav Gain"

# Update package list and install dependencies
RUN apt-get update && \
    apt-get install -y \
    software-properties-common \
    && rm -rf /var/lib/apt/lists/*

# Add Podman repository
RUN add-apt-repository -y ppa:projectatomic/ppa

# Update package list again and install Podman
RUN apt-get update && \
    apt-get install -y podman

# Step 1: Obtain the Ubuntu podman Image
# Download the latest Ubuntu podman image
RUN podman pull ubuntu

# For a specific version:
# RUN podman pull ubuntu:20.04

# List all podman images
RUN podman images

# Step 2: Run the Ubuntu podman Image
# Run the downloaded image in interactive terminal mode
CMD ["podman", "run", "-ti", "--rm", "ubuntu", "/bin/bash"]
