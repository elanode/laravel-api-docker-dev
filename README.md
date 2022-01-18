# Nuxt Docker Development

This repo is for building the laravel api docker image for Elanode's development process

## Includes
- Common Laravel (API Only) Development Environment
- Scheduler capability by supervisor

## Docker Compose Usage Example

```YAML 
version: "3"

services:
  php:
    image: "ghcr.io/elanode/laravel-api-docker-dev:latest"
    volumes:
      - ./api:/var/www/api

  supervisor:
    image: "ghcr.io/elanode/laravel-api-docker-dev:latest"
    volumes:
      - ./api:/var/www/api
      - ./docker/dev/logs/supervisor:/var/log
    depends_on:
      - php
    command: ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
```
