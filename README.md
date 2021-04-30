# ABOUT

This is a Rails environment created with Docker.

# Configuration

- Ruby on Rails
- Nginx
- Puma
- MySQL

# How to Use

## Copy And Rename Env File

```
cp .env.example .env
```

## Rails Project

If you have an existing project, place it under src.  
For a new project, enter this command from the console.

```
docker-compose run --rm rails rails new . --force --database=mysql --skip-test --skip-turbolinks
```

## Build And Start Container

In the console, do the this.

```
docker-compose up -d --build
```

### How to stop a container

```
docker-compose down
```

### Second or later activation

```
docker-compose up -d
```

## Set MySQL Connection Info

open `src/config/database.yml`.
Rewrite `default` as follows

```yml
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  database: <%= ENV.fetch('DB_DATABASE', 'rails') %>
  username: <%= ENV.fetch('DB_USERNAME', 'homestead') %>
  password: <%= ENV.fetch('DB_PASSWORD', 'secret') %>
  host: <%= ENV.fetch('DB_HOST', 'rails_db') %>
```

## Let's Enjoy Rails

Acess `http:localhost` in the browser.

# appendix

## Use VSCode Remote Container

With VSCode's RemoteContainer, you get a comfortable Rails integrated development environment.  
It comes with pre-configured sample files, so all you have to do is launch it.

Second, open the Remote Explorer from the sidebar of VSCode as a Container.

Next, click "Attach to Container" in the "rails-docker" selection field that appears.

Let's open "/var/www".

Have a pleasant development.
