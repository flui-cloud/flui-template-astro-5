# Flui Template — Astro 5

A minimal demo application built with **Astro 5** (static output) and ready to deploy on [Flui](https://flui.cloud).

This template includes:

- ⚡ Astro 5 with zero JS by default
- 🌐 Static output served via nginx
- 🩺 nginx `/health` endpoint
- 🐳 Multi-stage Dockerfile (`#flui-managed`)
- 📦 Long-cache headers for hashed assets
- 🎨 Themed landing page with Flui branding

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

1. Click **Use this template** on GitHub to create your own copy
2. Connect the new repository to Flui
3. Flui detects the `#flui-managed` Dockerfile and configures everything automatically
4. Click **Deploy** — your app is live in under a minute

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
