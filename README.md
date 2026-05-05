# flui-template-astro-5

Astro 5 static site template for Flui Cloud deployments.

## Local development

```bash
npm install
npm run dev        # http://localhost:4321
```

## Build

```bash
npm run build      # outputs to dist/
npm run preview    # preview the production build
```

## Docker

```bash
docker build -t my-astro-app .
docker run -p 8080:80 my-astro-app
# open http://localhost:8080
```

## Health check

`GET /health` → `{"status":"ok"}` (handled by nginx, always available)

## Endpoints

| Path | Description |
|------|-------------|
| `/` | Home page |
| `/health` | Health check (nginx) |

## Deployment

This template is deployed via [Flui Cloud](https://flui.cloud). The `Dockerfile` is managed by Flui (`# #flui-managed`) and rebuilt automatically on each push.
