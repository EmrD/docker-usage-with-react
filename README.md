

---

# React + Vite - Docker Usage

This document explains how to build your React project using Docker and how to transfer it to another production environment.

## Building the Project with Docker

1. **Create a Docker Image**

   Use the following command to build your React project with Docker. This will create a Docker image tagged as `my-app:latest`:

   ```bash
   docker build -t my-app:latest .
   ```

2. **Export the Docker Image as a Tar File**

   You can export the Docker image as a tar file, which can be used to transfer the image to another environment:

   ```bash
   docker save -o my-app.tar my-app:latest
   ```

## Transferring to Another Production Environment

The above steps will create a file named `my-app.tar`. This file allows you to move your Docker image to another production environment.

1. **Transfer the Tar File**

   Transfer the `my-app.tar` file to your new production environment (e.g., another server). You can use methods such as SCP, FTP, or any other file transfer tool.

2. **Load the Docker Image in the New Environment**

   On the new production environment, load the Docker image from the tar file:

   ```bash
   docker load -i my-app.tar
   ```

3. **Run the Docker Image**

   Once the image is loaded, you can run it. The following command will start the container and map port `80` of the host to port `80` of the container:

   ```bash
   docker run -p 80:80 my-app:latest
   ```

## Notes

- **Dockerfile**: Make sure a Dockerfile is present in your project's root directory, defining how the application should be built.
- **Port Configuration**: The `-p` parameter in the `docker run` command binds the host port to the container port. Adjust this parameter based on the ports your application uses.

---

This README file provides a step-by-step guide on Docker usage and transferring your project to a new environment, making it easier to manage and deploy your application.