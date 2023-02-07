## Docker container network for basic php app
All the commands have to be execute at the project root

### Create the network
    docker network create phpnetwork

### Create the phpfpm container
    docker container run -v ./src:/var/www/html -d --name phpfpm --network phpnetwork php:8.1-fpm

### Create the nginx container
    docker run -p 80:80 -d --name nginx --network phpnetwork -v ./src:/var/www/html -v ./nginx/logs:/var/log/nginx/ -v ./nginx/default.conf:/etc/nginx/con.d/default.conf nginx

### Set the permissions to execute the index.php file
    chmod 755 index.php

### Access to the web page
http://localhost
