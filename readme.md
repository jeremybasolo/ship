# SHIP

Ship is a quick and easy docker lemp or lamp stack, including :
- nginx
- apache
- php
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

## new-site.sh

To help me create new vhosts quickly, I created a ssh script than is tailored to my need : 
- Using nginx as the web server
- Running the setup on Windows 11 with WSL2 and Docker Desktop

Feel free to create it from the example file (`new-site.sh.example` => `new-site.sh`). Customize to your need, then give it the execution privilege and run it :
```
chmod +x new-site.sh
./new-site.sh
```

It accepts two parameters :
- Domain : `local-site.test`
- Path : `local-site`. This is the folder where the vhost needs to point to, from `/var/www/html/` in the container, so most likely `/home/USER_NAME/sites/` on your computer

For the Windows/WSL2 part, there is an extra dependency : `gsudo.exe`.  
It can be installed with a command to execute in **PowerShell** open as administrator:
```
PowerShell -Command "Set-ExecutionPolicy RemoteSigned -scope Process; [Net.ServicePointManager]::SecurityProtocol = 'Tls12'; iwr -useb https://raw.githubusercontent.com/gerardog/gsudo/master/installgsudo.ps1 | iex"
```

This allows the **shell script** to be run in the **WSL2 terminal** to edit the **hosts** file on **Windows**, so the local domain can point to **127.0.0.1**.