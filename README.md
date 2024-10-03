# Wordpress MySQL phpMyAdmin Docker Compose

This is a simple docker-compose file to run a Wordpress site with MySQL and phpMyAdmin.

## Requirements

- Docker
- Docker Compose

## Usage

- docker-compose up -d # Start the containers in the background
- docker-compose down --volumes # Remove all containers and volumes

## Deployment to EC2

EC2 instance:

- Create an EC2 instance with Amazon Linux 2 AMI
- `sudo yum update -y` # Update the system
- `sudo amazon-linux-extras install docker` # Install docker
- `start docker.service` # Start the docker service
- `sudo usermod -a -G docker ec2-user` # Add ec2-user to the docker group so we don't have to use sudo
- `mkdir downloads` # Create a directory for the project
- `cd downloads` # Change to the directory

Local machine:

- Ensure .pem file is in this directory (it is gitignored!)
- `chmod 400 "your-key.pem"` # Change the permissions of the key file
- `scp -i "your-key.pem" docker-compose.yml ec2-user@public_ip4_address:~/downloads`

EC2 instance:

- `sudo docker build -t ec2-wordpress -f .` # Build the image
- `sudo docker-compose up -d` # Start the containers in the background
- Confirm the site is running by visiting the public IP address in a browser!
- `sudo docker-compose down --volumes` # Remove all containers and volumes
