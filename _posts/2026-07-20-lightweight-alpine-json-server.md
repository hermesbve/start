---
title: "Lightweight Alpine-based json-server Docker Image"
date: 2026-07-20
categories:
  - Docker
  - DevOps
tags:
  - alpine
  - json-server
  - docker
  - rest-api
  - nodejs
  - alpine
  - json
  - docker
header:
  overlay_image: /assets/images/json-server-banner.png
  overlay_filter: 0.5
  caption: "JSON response from a live json-server demo"
---

[json-server](https://github.com/typicode/json-server) is a fantastic tool — get a full fake REST API with zero coding in less than 30 seconds.  
The go-to Docker image has long been [`clue/json-server`](https://hub.docker.com/r/clue/json-server) on Docker Hub, but it has some issues:

- **259 MB** in size (Debian-based full Node image)
- **8 years stale** — stuck on json-server v0.x from 2018
- No built-in healthcheck
- No `docker-compose` example

Time for a refresh.

## The Alpine rebuild

By switching the base image from Debian to `node:22-alpine`, we get a much leaner result:

| Image | Size | Reduction |
|---|---|---|
| `clue/json-server` (original) | **259 MB** | — |
| **this image** (Alpine) | **174 MB** | **–85 MB (33%)** |

The overhead beyond bare `node:22-alpine` (163 MB) is **only 11 MB** for the json-server package and its runtime dependencies. The Dockerfile is minimal:

```dockerfile
FROM node:22-alpine

RUN npm install -g json-server@latest --production

RUN mkdir -p /data
WORKDIR /data

RUN echo '{"placeholder": [{"id": "1", "message": "Mount your own /data/db.json"}]}' > /data/db.json

EXPOSE 3000

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD wget --no-verbose --tries=1 --spider http://localhost:3000/ || exit 1

ENTRYPOINT ["json-server"]
CMD ["db.json", "--host", "0.0.0.0", "--port", "3000"]
```

## Quick start

```bash
docker build -t json-server:alpine .
docker run -d -p 3000:3000 json-server:alpine
```

Or with your own data file:

```bash
docker run -d -p 3000:3000 \
  -v /path/to/your/db.json:/data/db.json \
  json-server:alpine
```

## Docker Compose

```yaml
services:
  json-server:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - ./data/db.json:/data/db.json
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "wget", "--no-verbose", "--tries=1", "--spider", "http://localhost:3000/"]
      interval: 30s
      timeout: 3s
      retries: 3
      start_period: 5s
```

## Generating realistic test data

A reusable seed script generates random data across 4 collections:

```bash
node data/generate-data.js > data/db.json
docker compose up -d --build
```

This populates 4 REST endpoints:

| Endpoint | Description |
|---|---|
| `GET /articles` | 15 articles with title, author, views, tags, status |
| `GET /comments` | 30 comments tied to articles via `postId` |
| `GET /users` | 10 users with name, email, department, role |
| `GET /products` | 8 products with price, rating, stock status |

All CRUD operations work out of the box:

```bash
curl http://localhost:3000/articles/1

curl -X POST -H 'Content-Type: application/json' \
  -d '{"title":"New Post","body":"Hello"}' \
  http://localhost:3000/articles

curl http://localhost:3000/users?_sort=-points

curl "http://localhost:3000/articles?_page=1&_per_page=5"

curl http://localhost:3000/articles?_embed=comments
```

## What's in the seed script

The `generate-data.js` script creates realistic data using randomly sampled names, cities, categories, and tags:

```javascript
const articles = [
  {
    id: "1",
    title: "Education Insights 2026",
    author: "Jack Rodriguez",
    views: 9366,
    status: "active",
    tags: ["javascript", "react", "node"]
  },
  // ... 15 articles total
];
```

## Key improvements over the upstream image

- **Smaller** — Alpine Linux saves 85 MB vs Debian
- **Up-to-date** — runs json-server v1.x (the latest) with all the new query features
- **Healthcheck** — Docker `HEALTHCHECK` monitors the server every 30s
- **Compose-ready** — pre-configured `compose.yaml` for easy lifecycle management
- **Seed script** — generates realistic test data with proper relations

## Query capabilities (json-server v1.x)

The newer json-server includes advanced querying:

| Feature | Example |
|---|---|
| Filter conditions | `GET /posts?views:gt=100` |
| Sort | `GET /posts?_sort=-views` |
| Pagination | `GET /posts?_page=1&_per_page=25` |
| Embed relations | `GET /posts?_embed=comments` |
| Complex queries | `GET /posts?_where={"or":[...]}` |

## Links

- [GitHub repo](https://github.com/BartVanEynde/json-server) with Dockerfile, seed script, and compose
- [json-server on GitHub](https://github.com/typicode/json-server)
- [clue/json-server on Docker Hub](https://hub.docker.com/r/clue/json-server)
