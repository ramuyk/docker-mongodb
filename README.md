# MongoDB Docker Container

## Introduction

This repository provides a `docker-compose.yml` configuration for deploying a MongoDB container using the [official MongoDB Community Server Docker image](https://hub.docker.com/r/mongodb/mongodb-community-server). This setup enables easy and quick deployment of a MongoDB instance for development or testing purposes.

## Repository Contents

This repository includes:

- **Docker Compose Configuration**: A `docker-compose.yml` file defining the MongoDB container.
  - **Persistent Data Storage**: Maps a local `./data/db` directory to `/data/db` in the container to persist MongoDB data across restarts.
  - **User Authentication**: Configures an initial admin user with a default username and password.
  - **Port Exposure**: Exposes MongoDB on port `27017` to allow connections from the host machine.
  - **Network Binding**: Uses `--bind_ip_all` to allow connections from any IP address within the network.

## Getting Started

### Quick Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/docker-mongodb.git
   cd docker-mongodb
   ```

2. **Start MongoDB**:
   Run the following command to start the MongoDB container:
   ```bash
   docker compose up -d
   ```

3. **Access MongoDB**:
   - Install `mongosh`:
     ```bash
      curl -fsSL https://pgp.mongodb.com/server-6.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-server-keyring.gpg
      echo "deb [signed-by=/usr/share/keyrings/mongodb-server-keyring.gpg] https://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
      sudo apt update && sudo apt install -y mongodb-mongosh
     ```
   - Connect using a MongoDB client or CLI:
     ```bash
     mongosh "mongodb://admin:admin@localhost:27017/?authSource=admin"
     ```
   - Alternatively, use a MongoDB GUI like **Compass** and connect to `mongodb://admin:admin@localhost:27017/`.

## Configuration Details

- **Port Mapping**: The container exposes MongoDB on `localhost:27017`. Modify the `ports` section in `docker-compose.yml` if needed.
- **Persistent Storage**: Data is stored locally in `./data/db` to ensure persistence.
- **Authentication**: Default admin credentials:
  - **Username**: `admin`
  - **Password**: `admin`
  
  It is recommended to change these credentials for security purposes after deployment.

