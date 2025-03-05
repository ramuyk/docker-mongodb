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
   - Connect using a MongoDB client or CLI:
     ```bash
     mongo --host localhost --port 27017 -u admin -p admin
     ```
   - Alternatively, use a MongoDB GUI like **Compass** and connect to `mongodb://admin:admin@localhost:27017/`.

4. **Stopping the Container**:
   To stop and remove the running container, use:
   ```bash
   docker compose down
   ```

## Configuration Details

- **Port Mapping**: The container exposes MongoDB on `localhost:27017`. Modify the `ports` section in `docker-compose.yml` if needed.
- **Persistent Storage**: Data is stored locally in `./data/db` to ensure persistence.
- **Authentication**: Default admin credentials:
  - **Username**: `admin`
  - **Password**: `admin`
  
  It is recommended to change these credentials for security purposes after deployment.

