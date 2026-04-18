# Next.js Static Export — Docker, GHCR & GitHub Actions

[![Next.js](https://img.shields.io/badge/Next.js-16-black?logo=next.js)](https://nextjs.org/)
[![Docker](https://img.shields.io/badge/Docker-Enabled-blue?logo=docker)](https://www.docker.com/)
[![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GH%20Actions-orange?logo=github-actions)](https://github.com/features/actions)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-black?logo=vercel)](https://vercel.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A robust boilerplate for students and developers to build a **Next.js** application, containerize it using a rootless **Nginx** setup, and automate the ship process using **GitHub Actions** with **Slack** notifications.

---

## Tech Stack

| Layer | Technology | Key Features |
| :--- | :--- | :--- |
| **Framework** | Next.js 16 | App Router, Static Export (`output: export`) |
| **Styling** | Tailwind CSS v4 | Cutting-edge utility-first styling |
| **Runtime** | Docker | Multi-stage builds, rootless security |
| **Registry** | GHCR.io | GitHub Container Registry for image hosting |
| **CI/CD** | GitHub Actions | Automated linting, building, and publishing |
| **Notifications** | Slack Webhooks | Real-time deployment status updates |

---

## Project Structure

```text
my-app/
├── .github/workflows/
│   └── ci-cd.yml        # GitHub Actions automated pipeline
├── app/                 # Next.js App Router (pages & styles)
├── public/              # Static assets (images, icons)
├── Dockerfile           # Industry-standard multi-stage build
├── nginx.conf           # Custom Nginx config (unprivileged)
├── compose.yml          # Local container orchestration
├── next.config.ts       # Static export configuration
└── package.json         # Scripts & dependencies
```

---

## Getting Started

### 1. Local Development
Clone the repository and install dependencies:
```bash
pnpm install
pnpm dev
```
Open [http://localhost:3000](http://localhost:3000) to view your app.

### 2. Static Build
Generate the production-ready static files:
```bash
pnpm build
```
Files will be exported to the `/out` directory.

### 3. Docker Local Testing
Test the exact environment used in production:
```bash
docker compose up -d --build
```
Your app will be served by Nginx at [http://localhost:8080](http://localhost:8080).

---

## CI/CD & Deployment

### GitHub Actions Pipeline
The pipeline is triggered on every **Pull Request** and **Push to Main**:
1. **Lint & Build**: Validates code quality and ensures static export works.
2. **Docker Publish**: Builds a production image and pushes it to GitHub Container Registry.
3. **Slack Alert**: Sends a beautiful Block Kit message to your Slack channel.

### Setting up Slack Notifications
1. Create a [Slack App](https://api.slack.com/apps).
2. Enable **Incoming Webhooks** and copy the URL.
3. Add it to your GitHub Repo: `Settings > Secrets > Actions > New repository secret`.
4. Name: `SLACK_WEBHOOK_URL`.

---

## Deploying to Vercel

This repository is optimized for Vercel's Edge Network:
1. Connect your GitHub repo to **Vercel**.
2. Vercel automatically detects the **Static Export** settings.
3. Enjoy instant global deployments.