# Docker LEMP 7 

A quick and easy way to setup your PHP application using Docker and docker-compose. This will setup a developement environment with PHP7-fpm, MariaDB and Nginx.

## Usage
~~~
git clone git@github.com:weop/docker-php7.git
cd docker-php7
docker-compose up
~~~

### Structure

~~~
├── app
│   └── public
│       └── index.php
├── database
├── docker-compose.yml
├── fpm
│   ├── Dockerfile
│   └── supervisord.conf
├── nginx
│   ├── Dockerfile
│   └── default.conf
~~~

- `app` is the directory for project files. Our Nginx config is pointing to `app/public`, which can be changed in `nginx/default.conf`
- `database` is where MariDB will store the database files.


credits:
shameerc/docker-php7.git