---
layout: page
title: "Configi"
permalink: /configi
---

# Configi

Zbiór ważnych konfiguracji i przykładów związanych z homelabem.

## Traefik – przykład konfiguracji (Docker Compose)

Fragment `docker-compose.yml` dla Traefika:

```yaml
version: "3.8"

services:
  traefik:
    image: traefik:v2.11
    container_name: traefik
    restart: unless-stopped
    command:
      - "--entrypoints.web.address=:80"
      - "--entrypoints.websecure.address=:443"
      - "--providers.docker=true"
      - "--providers.docker.exposedbydefault=false"
      - "--api.dashboard=true"
      - "--api.insecure=true"
      - "--log.level=INFO"
    ports:
      - "80:80"
      - "443:443"
      - "8085:8080"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
    networks:
      - proxy

networks:
  proxy:
    external: true
