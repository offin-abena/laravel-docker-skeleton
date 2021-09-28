# Laravel-Docker-Skeleton
## Laravel8, PHP8, Nginx, MySQL 8.0, Redis Docker Container
A complete Laravel, PHP Development environment that is very similar to production environment.

Docker Compose based **Laravel development environment** with individual **App** _(Laravel app)_, **Nginx**, **Database** _(MySQL)_, **Redis**  and **PHP** services.

## Installation
### Install Laravel
Clone the repo at your development machine. Go to your *Laravel-Docker-Skeleton* directory. Then Run this
```
A current version of laravel 8 is found in the ./src folder kindly feel free to make the required changes and develop your project


## Docker Container management

### Build containers
Run this to build your docker containers for each services (*app [php],web [nginx], mysql, redis*).
  ```

### Build and Run the containers
  ```
    docker-compose build && docker-compose up

  ```
 ### To Build and Run the services at background
  ```
     docker-compose build && docker-compose up -d

  ```
### SSH into your laravel application directory console
To **Start**, cd ./src _generate app key_ and _run migrations_, you need to ssh to your app container service. To ssh to your app container, run this.

```
    docker-compose exec app sh

```
This will take you to `/var/www/html` path inside your `app` service container. Now you can run your `composer install` and other Laravel or PHP specific commands there.

To ssh into other containers, replace the `app` with other container name as `mysql` e.g.
```
   docker-compose exec mysql sh

```

### Stop running containers
```
   docker-compose stop

```

### Pull down the  running containers
```
   docker-compose down

```
## Environment Variables
### PHP
Feel free to change the php docker image at `./docker/app/Dockerfile` file 
### MySQL
MySQL username, password can be changed from `docker-compose.yml` file under the  `environment` section of `mysql`. Change the value and build the mysql image again with `docker-compose build mysql`.
```
  environment:
    MYSQL_DATABASE: dev
    MYSQL_ROOT_PASSWORD: root
    MYSQL_USER: admin
    MYSQL_PASSWORD: secret
```
Now build and  restart the mysql service `docker-compose up mysql` to effect the changes. 
### Nginx
Feel free to the change the nginx configurations at `./nginx/default.dev.conf`
### Storage and Logs
This this implementation of docker uses `docker volume` and store some the docker container data at your host machine. Here is the details of folder structure and what data it contain:
- `./mysql` contain mysql database files
- `./cache/redis` contain redis database file
- `./nginx` contain nginx webserver configurations
### Connecting MySQL with local desktop client.
```
   host: 0.0.0.0
   username: user
   password: secret
   port: 4306
   
```
## Why Use Laravel Docker Skeleton
To be honest there are alot of docker skeletons for laravel out there? But I chose to create a new alternative based on the following:
1. This docker app images is based on `fm-alpine` based PHP image, which makes it very light weight.
2. This implementation uses the current version of laravel which is 8
3. It also uses MySQL 8
3. Last it comes with redis for caching and queueing 

## Browse your site locally
You can find your site running at http://localhost:8088

## TODO
Future development plan:
- [ ] Create a commandline utility for containerizing laravel and php application without installing the likes of  Windows Subsystem for Linux (WSL) for windows developers
- [ ] Abstract the implementation of docker containers for laravel developers

## Contribution
In case you find any vulnerabilities or "holes", kindly fork and PR your updates. I will be on standby to merge any reasonable PR.

### Contact
Email: `kobbi@simopay.com`

### Disclaimer
This docker skeleton for laravel is for development purposes.I do recommend it for Production yet.
