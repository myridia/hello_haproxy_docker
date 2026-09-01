# AGENTS.md — hello_haproxy_docker

## What this is
A Docker Compose example that proxies four HTTPS websites through a single HAProxy, backed by four nginx servers, using self-signed certificates from minica for testing.

## Stack
- Docker / Docker Compose
- HAProxy (reverse proxy, handles TLS)
- nginx (backends)
- minica (private CA for test certificates)

## Build / Run
```bash
cd dockers
docker-compose up
```
Add `/etc/hosts` entries (`127.0.0.1 ww1.app.local ww2.app.local ww3.app.local foo.local`) and trust `dockers/certs/minica.pem` locally.

## Structure
- `dockers/docker-compose.yml` — services (haproxy + 4 nginx)
- `dockers/haproxy.cfg` — HAProxy routing/TLS config
- `dockers/etc/nginx/` — backend nginx configs
- `dockers/certs/` — minica CA and per-domain certs
- `public/` — static content
- `assets/` — demo assets (screenshots/gifs)

## Conventions
- Requires a working Docker engine; commands must be run on the host with Docker.
- Certificates are test certs, not production credentials.
- Verify: `docker-compose config`
