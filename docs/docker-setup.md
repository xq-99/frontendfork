# Docker Setup Guide

This document provides instructions for setting up and using Docker with the **SelfSound** backend project.

## Prerequisites
Ensure that you have the following installed on your system:
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Running the PostgreSQL Database with Docker
To set up a PostgreSQL database using Docker, follow these steps:

1. **Ensure Docker is running**
2. **Navigate to the project root directory** where the `docker-compose.yml` file is located.
3. **Run the following command to start the database service:**

   ```sh
   docker-compose up -d
   ```

   This will start the PostgreSQL container in detached mode.

4. **Verify that the containers are running:**

   ```sh
   docker ps
   ```

   You should see a running `postgres` container and a `pgadmin` container if configured.

## Stopping the Containers
To stop the containers, run:

```sh
docker-compose down
```

This will stop and remove the containers but keep the database data.

## Accessing PostgreSQL via pgAdmin
If `pgAdmin` is included in `docker-compose.yml`, you can access it at:

- **URL:** [http://localhost:5050](http://localhost:5050)
- **Login:** `admin@selfsound.com`
- **Password:** `secret`

## Managing the Database
You can connect to the PostgreSQL database using the following credentials:

- **Host:** `localhost`
- **Port:** `5432`
- **Database:** `selfsound`
- **User:** `admin`
- **Password:** `secret`

To connect from the terminal, use:

```sh
docker exec -it <container_id> psql -U admin -d selfsound
```

## Removing Containers and Volumes
If you need to remove all containers and associated volumes:

```sh
docker-compose down -v
```

This will delete the database data, so use it with caution.

---
For further configuration, refer to `docker-compose.yml` and modify settings as needed.

