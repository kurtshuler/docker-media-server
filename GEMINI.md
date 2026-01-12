# GEMINI.md

## Project Overview

This project is a self-hosted media server setup using Docker and Traefik. It is based on the "Ultimate Docker Media Server (UDMS)" from SimpleHomelab, which is a fork of Deployarr. The project uses a `docker-compose.yml` file to define and manage a variety of services, which are exposed to the web using the Traefik reverse proxy.

## Key Services

The following services are included in this setup:

*   **Media Management:**
    *   Sonarr (TV shows)
    *   Radarr (movies)
    *   Lidarr (music)
    *   Readarr (books)
    *   Calibre-web (e-books)
*   **Downloaders:**
    *   SABnzbd
*   **Indexers:**
    *   Prowlarr
*   **Media Server:**
    *   Plex
*   **Utilities:**
    *   Traefik (reverse proxy)
    *   Authelia (authentication)
    *   Gluetun (VPN)
    *   Portainer (Docker management)
    *   Dozzle (log viewer)
    *   Glances (system monitoring)
    *   Uptime Kuma (status page)
    *   Notifiarr (notifications)
    *   FlareSolverr (Cloudflare solver)
    *   WUD (container update notifications)
*   **Paperless:**
    *   Paperless-ngx
    *   Paperless-ai
    *   Gotenberg
    *   Tika
*   **Database:**
    *   MariaDB
    *   Redis
*   **Other:**
    *   Adminer (database management)
    *   DDNS-Updater
    *   Cloudflare-Companion

## Networking

The project uses several Docker networks to isolate the services:

*   `default`: The default bridge network.
*   `socket_proxy`: A network for the Docker socket proxy.
*   `t3_proxy`: The Traefik network. Services that are exposed to the web are attached to this network.

## Configuration

The project is configured using a combination of files:

*   **`docker-compose-udms.yml`:** The main Docker Compose file, which includes the individual service definitions from the `compose/udms/` directory.
*   **`.env`:** An environment file (not present in the analysis, but inferred from the compose files) that contains environment variables for configuring the services.
*   **`compose/udms/`:** This directory contains the individual Docker Compose files for each service.
*   **`appdata/traefik3/rules/udms/`:** This directory contains the Traefik routing rules, which define how the services are exposed to the web.

## Building and Running

To run the project, you will need to have Docker and Docker Compose installed.

**Starting the services:**

```bash
docker-compose -f docker-compose-udms.yml up -d
```

**Stopping the services:**

```bash
docker-compose -f docker-compose-udms.yml down
```

**Viewing the logs:**

```bash
docker-compose -f docker-compose-udms.yml logs -f <service_name>
```
