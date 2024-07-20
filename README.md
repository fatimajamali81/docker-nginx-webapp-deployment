# Basic Web Application Deployment

This project demonstrates the deployment of a basic web application using Docker, Nginx, and an AWS EC2 instance.

## Setup

1. **AWS EC2 Instance Setup:**
   - Launch an EC2 instance with Ubuntu.
   - Open ports 22 (SSH) and 80 (HTTP) in the security group.

2. **Install Docker:**
   - Update the package list and install Docker:
     ```bash
     sudo apt update
     sudo apt install -y docker.io
     sudo systemctl start docker
     sudo systemctl enable docker
     ```

3. **Build and Deploy:**
   - Create project files (HTML and Dockerfile).
   - Build the Docker image:
     ```bash
     sudo docker build -t my-webapp .
     ```
   - Run the Docker container:
     ```bash
     sudo docker run -d -p 80:80 my-webapp
     ```

4. **Verify Deployment:**
   - Navigate to the public DNS of your EC2 instance to view the deployed web application.

## Files

- `index.html`: The HTML content for the web application.
- `Dockerfile`: Dockerfile for building the Nginx image.

## License

This project is licensed under the MIT License.
