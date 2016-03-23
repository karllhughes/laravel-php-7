# Dockerfile for Laravel 5.1+ and PHP 7.0

This Docker container builds the latest version of PHP 7.0 on Ubuntu as well as all the PHP extensions needed for Laravel 5.1+. It also includes composer and some nice command line apps like vi for debugging/editing files.

I took pieces from Heroku's PHP 7.0 buildpack and a couple other PHP 7.0 Docker containers that I found. I welcome pull requests or suggestions for improvements on the Github Repo.

### Running this Container
*Note: I'm assuming you've set up Docker and a VM (if necessary). If not, 
start [here](https://docs.docker.com/engine/installation/).*

- Navigate to the root of your Laravel project
- Currently you have to update the /storage folder permissions to 777. This is due to the fact that the docker container mounts the whole volume of your Laravel application.
- Download the latest version of the base PHP7/Laravel Docker container: `docker pull karllhughes/laravel-php-7`
- From the root of your Laravel project, run `docker run -it -v $PWD:/www -p 80:80 karllhughes/laravel-php-7` to bring up the container's command line.
- From the container's command line, run any of the following commands:
    - `cd /www` to navigate to the web root
    - `apachectl start` (must be run to start Apache)
    - `composer install` or `composer update`
    - `php vendor/bin/phpunit` to run unit tests
- View your Laravel project by going to `localhost` or the IP address of your Virtualbox or server that's running Docker.
