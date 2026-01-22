# Todo App on AWS (Containerized)

A simple Todo application built with Node.js, Express, and EJS, designed to be containerized with Docker and deployed to AWS.

## Repository
[https://github.com/Abishek-04/todo_aws_docker](https://github.com/Abishek-04/todo_aws_docker)

## Features
- **Add & Delete Todos**: Simple interface to manage tasks.
- **Data Persistence**: Uses a JSON file (`data.json`) to store todos.
- **Dockerized**: specific `Dockerfile` and `docker-compose.yml` for easy setup.
- **AWS Ready**: Deployment guide included for AWS EC2.

## How to Run Locally

### Using Docker (Recommended)
You need to have Docker installed.

1.  Clone the repository:
    ```bash
    git clone https://github.com/Abishek-04/todo_aws_docker.git
    cd todo_aws_docker
    ```
2.  Start the application:
    ```bash
    docker compose up -d --build
    ```
3.  Open your browser at `http://localhost:3000`.
4.  To stop: `docker compose down`.

### Using Node.js directly
1.  Install dependencies: `npm install`
2.  Start the app: `npm start`

## Deployment (EC2 or Dedicated Server)

1.  **Prepare your Server**:
    - Ensure you have a Linux server (Ubuntu, Amazon Linux, etc.).
    - Install Docker and Git.
    - Ensure **Port 3000** is open (Security Group in AWS or Firewall).

2.  **Deploy**:
    SSH into your server and run:
    ```bash
    # Clone the repo
    git clone https://github.com/Abishek-04/todo_aws_docker.git
    cd todo_aws_docker

    # Start the app
    docker compose up -d --build
    ```

3.  **Access**:
    Go to `http://<your-server-ip>:3000`

For a more detailed AWS-specific guide, check [DEPLOY_GUIDE.md](./DEPLOY_GUIDE.md).
