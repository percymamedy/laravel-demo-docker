<h1 align="center">Laravel Docker Demo</h1>

## About Laravel Docker Demo

Laravel Docker Demo is a small Demo App built with Laravel. The aim of this demo is to 
demonstrate working and developing a PHP App under a docker environment.

## About Docker

Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate 
your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage 
your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s 
methodologies for shipping, testing, and deploying code quickly, you can significantly 
reduce the delay between writing code and running it in production.

Learn more about Docker [here](https://www.docker.com/)

## Installation

### Install Docker & Docker Compose

Make sure you have [Docker](https://docs.docker.com/engine/installation/) and [Docker Compose](https://docs.docker.com/compose/install/). If you don't follow
the installation guide on Docker website it's pretty easy to get started with.

### Build and run your Containers

To get started developing start by running your containers. Open up a terminal and cd in the root of the project. i.e where the ```docker-compose.yml``` file
is located at.

Now type the following command:

```bash
$ docker-compose up -d
```

This command will take care of building up your container images (if not already built), create them and run them.
Notice the ```-d``` which means daemon or detached. This option will run your containers in the background so that your Terminal might not be block. 
If you'd like more verbose output of you can omit the ```-d``` option. 

### Installing your Laravel Dependencies

Exec in the web container as the ```www-data``` user.

```bash
$ docker-compose exec --user=www-data web bash
```

Install composer dependencies

```bash
$ composer install
```

Create your .env file:

```bash
$ cp .env.example .env
```

Set your application Key

```bash
$ php artisan key:generate
```

You are now all set to go!!..
 
If you would like to learn more about Laravel check out the docs [here](https://laravel.com)

## License

Laravel Docker Demo is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
