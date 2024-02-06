
# Running Ubuntu with Podman in Docker

This repository contains files to set up and run an Ubuntu container with Podman inside using Docker Compose. It also demonstrates data persistence between the host and the container.

## Getting Started

Follow the instructions below to set up and run the Docker Compose setup.

### Prerequisites

- Docker installed on your system. You can download and install Docker from [the official Docker website](https://www.docker.com/get-started).
- Docker Compose installed on your system. If you haven't installed it yet, you can follow the instructions [here](https://docs.docker.com/compose/install/).

### Installation

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your_username/ubuntu-podman-docker.git
   ```

2. Navigate to the cloned repository:

   ```bash
   cd ubuntu-podman-docker
   ```

3. Create a directory named `podman_Share`:

   ```bash
   mkdir podman_Share
   ```

## Usage

To build and run the Docker Compose setup, execute the following command:

```bash
docker-compose up --build
```

This command will build the Docker image with Podman installed and run the Ubuntu container with Podman inside. It will also mount the `podman_Share` directory on the host to the `/data` directory in the container, allowing data persistence between the host and the container.

To stop the Docker Compose setup, use:

```bash
docker-compose down
```

## Contributing

Contributions are welcome! If you find any issues or improvements, feel free to open a pull request.

## License

This project is licensed under the [MIT License](LICENSE).


