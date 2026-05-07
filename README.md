# Flui Template — Astro 5

A minimal demo application built with **Astro 5** (static output) and ready to deploy on [Flui](https://flui.cloud).

Includes:

- Astro 5 with zero JS by default
- Static output served via nginx
- nginx `/health` endpoint
- Multi-stage `#flui-managed` Dockerfile
- Long-cache headers for hashed assets
- Themed landing page

## Local development

```bash
npm install
npm run dev
```

App runs on http://localhost:4321

## Build with Docker

```bash
docker build -t flui-demo-astro .
docker run -p 8080:80 flui-demo-astro
```

Then visit:

- http://localhost:8080 — homepage
- http://localhost:8080/health — health check (nginx)

## Environment variables

See [.env.example](.env.example) for available variables. None are required for the demo to run.

| Variable | Default | Description |
|----------|---------|-------------|
| `APP_NAME` | `Flui Demo Astro` | Application name shown on the homepage |
| `APP_VERSION` | `1.0.0` | Application version |
| `PORT` | `80` | nginx port |

## Deploy with Flui

This repo ships with a [`flui.yaml`](./flui.yaml) manifest describing the build strategy, port, healthcheck and resource profile.

From the CLI, with `flui` installed and authenticated against your cluster:

```bash
flui deploy ./flui.yaml
```

The CLI reads the manifest, triggers a build via GitHub Actions and rolls out the workload.

From the UI:

1. Click **Use this template** on GitHub.
2. Connect the new repository to Flui.
3. Click **Deploy**.

Built for [Flui](https://github.com/flui-cloud/flui.api) — see the main repo for cluster setup and CLI installation.

## Project structure

```
.
├── src/
│   ├── layouts/
│   │   └── Layout.astro    # Base HTML layout
│   ├── pages/
│   │   └── index.astro     # Homepage
│   └── env.d.ts
├── public/
│   └── favicon.svg
├── nginx/
│   └── default.conf        # SPA fallback + /health endpoint
├── Dockerfile              # #flui-managed multi-stage build
├── astro.config.mjs
├── tsconfig.json
└── package.json
```

## License

MIT
