# 2048 Dockerized Application

## Overview

This repository contains the source code for a Dockerized version of the 2048 game application. The application is based on the popular 2048 game created by Gabriele Cirulli and is deployed using Docker and AWS Elastic Beanstalk for easy scalability and management.

## Dockerfile

The Dockerfile in this repository defines the environment and dependencies needed to run the application. Here is the content of the Dockerfile:

```Dockerfile
FROM ubuntu:22.04

RUN apt-get update && \
    apt-get install -y nginx zip curl && \
    echo "daemon off;" >> /etc/nginx/nginx.conf && \
    curl -o /var/www/html/master.zip -L https://github.com/gabrielecirulli/2048/archive/refs/heads/master.zip && \
    cd /var/www/html && \
    unzip master.zip && \
    mv 2048-master/* . && \
    rm -rf 2048-master master.zip

EXPOSE 80
CMD ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]

** Local Development **

To run the application locally using Docker, follow these steps:

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/your-username/repository-name.git
    cd repository-name
    ```

2. Build the Docker image:

    ```bash
    docker build -t 2048-dockerized .
    ```

3. Run the Docker container:

    ```bash
    docker run -p 8080:80 2048-dockerized
    ```

4. Access the application in your web browser at `http://localhost:8080`.


** Deployment to AWS Elastic Beanstalk **
Step 1: To deploy the application to AWS Elastic Beanstalk, follow these steps:
Step 2: Push the code to the Elastic Beanstalk application environment.
Step 3: After reviewing the configurations proceed to start the deployment.

