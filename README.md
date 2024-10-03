# Wordpress MySQL phpMyAdmin Docker Compose

This is a simple docker-compose file to run a Wordpress site with MySQL and phpMyAdmin.

## Requirements

- Docker
- Docker Compose

## Usage

- docker-compose up -d # Start the containers in the background
- docker-compose down --volumes # Remove all containers and volumes

## Deployment to VPS

- Install Docker and Docker Compose on your VPS
- Copy the docker-compose.yml file to your VPS
- Run `docker-compose up -d` to start the containers
- Visit your VPS IP address in your browser to access the Wordpress site
- Visit your VPS IP address followed by `:8080` to access phpMyAdmin
