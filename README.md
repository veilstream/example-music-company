# VeilStream Example
This is an example of how to use VeilStream for a preview environment

## Usage

### 1) fork the repo
### 2) login to [app.veilstream.com](app.veilstream.com)
### 3) connect the cloned repository to VeilStream at [app.veilstream.com/onboarding](app.veilstream.com/onboarding)
### 4) click "Complete Setup"
![click complete setup](./docs/Screenshot_20260202_211202.png)
### 5) click "Deploy from Main"
![click deploy from main](./docs/Screenshot_20260202_211435.png)
### 6) go to the 3 dots menu, settings, and update the app container's env var to be `{{api-external-url}}`
![set env var](./docs/Screenshot_20260202_211850.png)
### 7) create an environment off your main branch
### 8) wait for the deployment
### 9) review the deployed version of this application

## CI: wait for preview (GitHub Actions)

[`.github/workflows/preview-smoke.yml`](.github/workflows/preview-smoke.yml) waits for the VeilStream preview for the PR commit (without starting a second deploy), then curls the frontend and API.

The wait step uses the public [`veilstream/veilstream-github-action`](https://github.com/veilstream/veilstream-github-action) Action (defaults to the PR head SHA so it matches the App deploy).

Required repository secret:

| Secret | Purpose |
|--------|---------|
| `VEILSTREAM_API_KEY` | Org REST or MCP API key (read is enough) for the **do-sfo** data center (`api-sfo.veilstream.com`) |

Open a PR against this repo (with the GitHub App connected) to exercise the workflow.

## What this example application is:

It's the chinook dataset used to populate a postgres database, representing a music company. The app container is a react app that is the frontend talking to a simple fastapi api container backed by the postgres database.
