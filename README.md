# RSS Reader

Research and planning for a self-hosted RSS reader to replace the Google Reader experience.

## Goal

Run an RSS reader locally with Docker -- no domain, SSL, or reverse proxy needed. Just a single `docker run` command and open it in a browser.

## Top Picks

| App | Style | RAM | Docker Complexity | Notes |
|-----|-------|-----|-------------------|-------|
| [Fusion](https://github.com/0x2E/fusion) | Minimalist (Go/Svelte) | ~50 MB | 1 container, SQLite | Simplest to run |
| [CommaFeed](https://github.com/Athou/commafeed) | Closest to Google Reader | ~128 MB | 1 container, embedded H2 | Best classic UI |
| [FreshRSS](https://github.com/FreshRSS/FreshRSS) | Feature-rich (PHP) | ~128 MB | 1 container, SQLite | Most popular, best mobile support |
| [Miniflux](https://github.com/miniflux/v2) | Minimalist (Go) | ~64 MB + PG | 2 containers (app + PostgreSQL) | Fast, lean |

## Quick Start

Pick one and run it (requires Docker):

```bash
# Fusion (simplest, ~50 MB RAM)
docker run -d -p 8080:8080 -v fusion:/data -e FUSION_PASSWORD="yourpassword" ghcr.io/0x2e/fusion:latest

# CommaFeed (closest to Google Reader, ~128 MB RAM)
docker run -d -p 8082:8082 -v commafeed:/commafeed/data athou/commafeed

# FreshRSS (most features, ~128 MB RAM)
docker run -d -p 8080:80 -e 'CRON_MIN=1,31' -v freshrss_data:/var/www/FreshRSS/data freshrss/freshrss
```

Then open `http://localhost:8080` (or `:8082` for CommaFeed) in your browser.

## Status

Research phase. The full survey of self-hosted and desktop RSS readers is in `readme.log`. Next step: pick one to install or build a custom reader.
