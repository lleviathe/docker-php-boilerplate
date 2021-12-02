
# Ready to use Docker Compose boilerplate for PHP projects
If you're tired of manually configuring the docker-compose stack for every new project, now it's time to use the boilerplate. A boilerplate is any software solution that can be reused in new contexts without significant changes to the original, which increases your development speed by reducing the count of routine tasks.

## Stack:

- php-fpm with `mbstring, zip, exif, pcntl, pdo_pgsql, xsl, redis` and `gd`  extensions (`8.1` stable version included, fully compatible with `7.4/8.0`)
- Nginx webserver with configured FastCGI (Default exposed port: `8001`)
- PostgreSQl DBMS
- Redis
- PgAdmin 4 (ultimate web UI for PostgreSQL) (Default exposed port: `8080`)

## Usage:
With Github's template repositories feature, you can create your own repository using this template and configure it with instruction shown below, just change the `lleviathe` to your GitHub username. Read more: https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template

First of all, of course, you need to install and configure Docker and docker-compose on your machine. Read more: https://docs.docker.com/get-docker/

**Clone & navigate to the repository using Git:**

    git clone https://github.com/lleviathe/docker-php-boilerplate.git your-project-name && cd your-project-name

   
  **ATTENTION**: *You have to change the network and containers base name in  `docker-compose.yml` to your project name. It's not required, but I recommend doing this for aesthetic reasons.*
  **Build and set up docker-compose stack:**

    docker-compose up --build

**Using the `app` service's shell, create a new composer project (e.g Laravel):**

    docker-compose exec app composer create-project laravel/laravel .
**If you already have project files in `src` directory without installed dependencies, just install them by command below:**

    docker-compose exec app composer install
You're ready to code! Now you can access your project on `http://localhost:8001` and PgAdmin on `http://localhost:8080` using the credentials, provided in `docker-compose.yml`

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.