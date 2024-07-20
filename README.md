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


## Optional step: Set Up Portainer for Docker Management

Portainer provides a graphical user interface for managing Docker containers. This step is optional but recommended for users who prefer a UI for Docker management.

1. **Pull and Run the Portainer Docker Image:**
   - Pull the Portainer image:
     ```bash
     sudo docker pull portainer/portainer-ce
     ```
   - Run Portainer with Docker:
     ```bash
     sudo docker run -d -p 9000:9000 -p 9443:9443 --name portainer \
       --restart always \
       -v /var/run/docker.sock:/var/run/docker.sock \
       -v portainer_data:/data \
       portainer/portainer-ce
     ```

2. **Access Portainer:**
   - Open your browser and navigate to `http://your-ec2-public-dns:9000` for HTTP or `https://your-ec2-public-dns:9443` for HTTPS (ensure you set up a secure connection if using HTTPS).

3. **Initial Portainer Setup:**
   - You will be prompted to create an admin user with a password. Complete this setup to access Portainer’s dashboard.

4. **Using Portainer:**
   - Log in to Portainer with the admin credentials you set up.
   - Explore Docker containers, images, networks, and volumes through the Portainer dashboard.

5. **Updating Portainer:**
   - To update Portainer, stop and remove the existing container, and pull the latest image:
     ```bash
     sudo docker stop portainer
     sudo docker rm portainer
     sudo docker pull portainer/portainer-ce
     sudo docker run -d -p 9000:9000 -p 9443:9443 --name portainer \
       --restart always \
       -v /var/run/docker.sock:/var/run/docker.sock \
       -v portainer_data:/data \
       portainer/portainer-ce
     ```


## Files in Project

- `index.html`: The HTML content for the web application.
- `Dockerfile`: Dockerfile for building the Nginx image.

## License

This project is licensed under the MIT License.
