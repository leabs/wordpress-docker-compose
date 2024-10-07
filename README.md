# Wordpress MySQL phpMyAdmin Docker Compose

This is a simple docker-compose file to run a Wordpress site with MySQL and phpMyAdmin that can be deployed to an EC2 instance (Amazon Linux 2 AMI).

## Usage

_Note_: If you're using an M series mac, you need to install Rosetta with:
`softwareupdate --install-rosetta` if you wish to build locally. The images are set to "platform: linux/amd64" for maximum compatibility.

- If you want to try it locally, you can clone this repo and simply run `docker-compose up` assuming you have docker installed with the `wordpress`, `mysql`, and `phpmyadmin` images running.

## Deployment to EC2

EC2 instance:

- Create an EC2 instance with Amazon Linux 2 AMI
- `sudo yum update -y` # Update the system
- `sudo amazon-linux-extras install docker` # Install docker
- `start docker.service` or `sudo systemctl start docker` # Start the docker service
- `sudo usermod -a -G docker ec2-user` # Add ec2-user to the docker group so we don't have to use sudo
- You must restart and log back in after making user group changes with `exit`
- `mkdir downloads` # Create a directory for the project
- `cd downloads` # Change to the directory

Local machine:

- Clone this repository to your local machine
- Copy AWS .pem file is in this directory (it is gitignored!)
- `chmod 400 "your-key.pem"` # Change the permissions of the key file if needed
- `scp -i "your-key.pem" docker-compose.yaml ec2-user@public_ip4_address:~/downloads`

EC2 instance:

- `sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose` # Download docker-compose
- `sudo chmod +x /usr/local/bin/docker-compose` # Make docker-compose executable
- `docker-compose up` # Start the containers!

#### Extra commands:

- `sudo systemctl enable docker` Enable Docker to start on boot (optional)
