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

## Build

In the console, do the this.

```
make build
# OR
docker-compose build
```

## Rails Project

If you have an existing project, place it under src.
For a new project, enter this command from the console.

```
docker-compose run --rm rails rails new . --force --database=mysql --skip-test --skip-turbolinks
```
※First time installation is long

## Start Container

In the console, do the this.

```
make up
# OR
docker-compose up -d
```

## Let's Enjoy Rails

Acess `http:localhost:8080` in the browser.
