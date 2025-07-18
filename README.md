# ByteSizer Demos

**ByteSizer is a tool to create data subsets for testing, analytics, and machine learning workflows.**

[![Docker Pulls](https://img.shields.io/badge/docker-ready-blue)](https://github.com/orgs/ruyasoft/packages/container/package/bytesizer)

This repository contains sample datasets and configuration templates to demonstrate the capabilities of [ByteSizer](https://bytesizer.ai).

## Contents

- [`driver_test_scores`](driver_test_scores/README.md): Sample data for drivers license test scores
- [`flight_rewards`](flight_rewards/README.md): Sample data for an airline rewards program

Use these samples to test ByteSizer locally or in your demo/on-prem environments.

## Repository Structure

```
.
├── driver_test_scores/
│   ├── configs/
│   ├── input_data/
│   └── README.md
├── flight_rewards/
│   ├── configs/
│   ├── input_data/
│   └── README.md
└── README.md
```

## About ByteSizer
ByteSizer is provided as a lightweight Docker image that makes it easy to run data subsetting workflows across different datasets and environments. It requires Docker to be installed on the host machine.

## Prerequisites

### Installing Docker
To use ByteSizer, ensure that Docker is installed on your system:

* For macOS and Windows: Install [Docker Desktop](https://www.docker.com/products/docker-desktop), which includes everything needed to run containers with a graphical interface for managing them.

* For headless Linux systems (e.g. cloud servers, WSL, or minimal installations): Install the Docker Engine using the appropriate package manager for your distribution (e.g. `apt`, `yum`, `dnf`).

After installation, you can verify Docker is working by running:
```shell
docker --version
```

### Pulling the ByteSizer Docker Image
Once Docker is set up, you can pull the latest demo-ready ByteSizer image using:

```shell
docker pull ghcr.io/ruyasoft/bytesizer:beta
```
This image includes all necessary dependencies and runtime components.

## Running ByteSizer
Each dataset or example in this repository (e.g., [`driver_test_scores`](driver_test_scores/README.md), [`flight_rewards`](flight_rewards/README.md)) includes its own `README.md` file with instructions for how to run ByteSizer on that specific dataset. These instructions describe how to mount the appropriate data and configuration files into the container and execute a sample run.

## License

This project is licensed under the terms described in the [LICENSE](LICENSE.txt) file.

## Need Help?

Open an issue or contact us at support@bytesizer.ai.
