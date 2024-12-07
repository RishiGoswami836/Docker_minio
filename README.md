# MinIO Docker Setup and Usage

## Introduction

MinIO is an open-source, high-performance, distributed object storage service designed to be scalable and compatible with the Amazon S3 API. It allows you to store large amounts of unstructured data, such as photos, videos, backups, and logs. With MinIO, you can easily create a private cloud storage solution with minimal setup.

This project demonstrates how to deploy MinIO as a containerized service using Docker, manage the data, and access it through both the web console and API.

## Learning Objectives

- **Docker**: Learn how to run MinIO as a Docker container.
- **MinIO**: Understand how to use MinIO as an object storage service.

## Prerequisites

- **Docker**: Make sure Docker is installed on your system. [Docker Installation Guide](https://docs.docker.com/get-docker/)
- **Optional: Docker Compose**: Use Docker Compose for easier management of the MinIO container. [Docker Compose Installation Guide](https://docs.docker.com/compose/install/)
- **Optional: AWS CLI**: Install AWS CLI to interact with MinIO through the command line. [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

## Steps to Set Up MinIO with Docker

### 1. **Pull the MinIO Docker Image**

First, pull the latest MinIO Docker image from Docker Hub:

    docker pull minio/minio:latest

### 2. **Run MinIO Container**

Start a MinIO container using the following command:

    docker run -d --name minio -p 9000:9000 -p 9001:9001 \
      -e MINIO_ROOT_USER=minioadmin \
      -e MINIO_ROOT_PASSWORD=minioadmin123 \
      minio/minio server /data --console-address ":9001"

#### **Explanation**:

- `-d`: **Run the container in detached mode**.
- `--name minio`: **Names the container "minio"**.
- `-p 9000:9000`: **Maps the MinIO API port**.
- `-p 9001:9001`: **Maps the MinIO Web Console port**.
- `-e MINIO_ROOT_USER=minioadmin`: **Set the MinIO root user**.
- `-e MINIO_ROOT_PASSWORD=minioadmin123`: **Set the MinIO root password**.
- `server /data --console-address ":9001"`: **Starts MinIO and sets the data storage location**.

### 3. **Verify Running Containers**

To check if MinIO is running, use the following command:

    docker ps

This will display all active containers. Look for minio in the list.

### 4. **Access the MinIO Web Console**

MinIO provides a web interface to manage your data. Open your web browser and navigate to:

[http://localhost:9001](http://localhost:9001)

#### **Login with the following credentials**:
- **Username**: minioadmin
- **Password**: minioadmin123

### 5. **Create a Bucket**

Once logged in, you can create a new bucket by clicking the **Create Bucket** button and giving it a name.

### 6. **Upload Files**

You can upload files to your newly created bucket by clicking the Upload button and selecting files from your local machine.

### 7. **Delete files and Bucket**

You can also delete the uploaded file from the bucket folder and after removing the files the bucket can be deleted.


## Conclusion

This project demonstrates how to quickly set up and use MinIO as a containerized object storage solution using Docker. With MinIO, you can store and manage large amounts of unstructured data, all while maintaining S3 compatibility for easy integration into your applications.

## Future Improvements

- **Backup & Restore**: Learn how to backup and restore MinIO data.
- **Advanced Configuration**: Explore advanced MinIO features such as distributed setup and high availability.
- **Docker Compose**: Use Docker Compose to automate and simplify multi-container setups.

## References

[MinIO on Docker Hub](https://hub.docker.com/r/minio/minio)

