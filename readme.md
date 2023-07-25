# SHIP

Ship is a quick and easy docker lemp or lamp stack, including :
- nginx
- apache
- php 7.4
- php 8.1
- mysql
- mailhog
- phpmyadmin

## Usage

Clone this repo. Create a `docker-compose.yml` based on `docker-compose.yml.example` and customize it to your needs.

When done, you can run `docker-compose up -d` to start all the containers. 

To stop them, just run `docker-compose down`.

You can create virtual hosts in the `vhosts` of nginx or apache. Restart the containers for the changes to take effect.
You will have to add the right domains to you hosts file on your system.

The `root` password to MySQL is `docker` by default.