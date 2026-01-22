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

## Deployment
See the [DEPLOY_GUIDE.md](./DEPLOY_GUIDE.md) for step-by-step instructions on deploying to an AWS EC2 instance (Ubuntu/Amazon Linux).
