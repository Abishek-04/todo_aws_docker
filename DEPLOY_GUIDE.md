# EC2 Deployment Guide for Dockerized Todo App (Ubuntu)

This guide will walk you through deploying your Todo application to an AWS EC2 instance running **Ubuntu**.

## Prerequisites
- An AWS Account
- The Git repository URL for your project

## Step 1: Launch an EC2 Instance

1.  Log in to the **AWS Management Console**.
2.  Navigate to **EC2** and click **Launch Instance**.
3.  **Name**: Give it a name (e.g., `todo-app-server`).
4.  **AMI**: Select **Ubuntu** (Ubuntu Server 24.04 LTS or 22.04 LTS).
5.  **Instance Type**: `t2.micro` (Free tier eligible) is sufficient.
6.  **Key Pair**: Select an existing key pair or create a new one (and save the `.pem` file).
7.  **Network Settings**:
    *   Check "Allow SSH traffic from".
    *   Check "Allow HTTP traffic from the internet" (optional, but good practice).
8.  **Storage**: Default (8GB) is fine.
9.  Click **Launch Instance**.

## Step 2: Configure Security Group (Open Port 3000)

Your app runs on port 3000, so you must explicitly allow traffic on this port.

1.  Go to the **EC2 Dashboard** -> **Instances**.
2.  Select your new instance.
3.  Click the **Security** tab -> Click the **Security Group ID**.
4.  Click **Edit inbound rules**.
5.  Click **Add rule**:
    *   **Type**: Custom TCP
    *   **Port range**: `3000`
    *   **Source**: `Anywhere-IPv4` (`0.0.0.0/0`)
6.  Click **Save rules**.

## Step 3: Connect to your Instance

Open your terminal (or Putty) and connect using your key pair. Note the username is `ubuntu` for Ubuntu AMIs.

```bash
chmod 400 <path-to-your-key.pem>
ssh -i <path-to-your-key.pem> ubuntu@<your-ec2-public-ip>
```

## Step 4: Install Docker and Git

Once connected to the EC2 instance, run the following commands:

```bash
# Update the package list
sudo apt-get update

# Install Git and Docker
sudo apt-get install -y git docker.io docker-compose-v2

# Start Docker service (usually starts automatically on Ubuntu, but good to be sure)
sudo systemctl start docker
sudo systemctl enable docker

# Allow 'ubuntu' user to run Docker commands without sudo
sudo usermod -a -G docker ubuntu
```

> [!IMPORTANT]
> **Log out and log back in** for the permission changes to take effect:
> Type `exit` and then SSH in again.

## Step 5: Deploy the Application

Now, clone your repo and run the container.

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/Abishek-04/todo_aws_docker.git
    cd todo_aws_docker
    ```
    *(Note: use the actual folder name created by git clone if it differs)*

2.  **Start the Application**:
    ```bash
    docker compose up -d --build
    ```

## Step 6: Verify

Open your browser and visit:
`http://<your-ec2-public-ip>:3000`

You should see your Todo App!

## Troubleshooting

- **Permissions Error?** If you see "permission denied" when running docker, make sure you ran the `usermod` command and **re-logged in**.
- **Site can't be reached?** Double-check **Step 2**. The Security Group MUST allow inbound traffic on port 3000.
