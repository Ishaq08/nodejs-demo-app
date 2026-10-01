# nodejs-demo-app: CI/CD with GitHub Actions

## Objective
Automate testing, building and deployment of a Node.js web app using a CI/CD pipeline.

## Tools
GitHub, GitHub Actions, Node.js (Express, Jest), Docker, Docker Hub

## Pipeline (`.github/workflows/main.yml`)
Triggered on every push to `main`:
1. **test**: checkout, set up Node 20, `npm ci`, `npm test`
2. **build-and-push** (runs only if tests pass): log in to Docker Hub, build the image, push `latest` and commit-SHA tags

## Setup
1. Run `npm install` once locally to generate `package-lock.json`, and commit it.
2. Add repo secrets under Settings, Secrets and variables, Actions:
   - `DOCKERHUB_USERNAME`
   - `DOCKERHUB_TOKEN` (Docker Hub access token)
3. Push to `main` and check the **Actions** tab.

## Run locally
```bash
npm install
npm test
npm start            # http://localhost:3000
docker build -t nodejs-demo-app .
docker run -p 3000:3000 nodejs-demo-app
```

## Screenshots
Add screenshots of the green Actions run and the image on Docker Hub here.

## What I learned
Coming from Jenkins: workflow file instead of Jenkinsfile, jobs instead of stages, runners instead of agents, and repository secrets instead of the Jenkins credentials store.
# nodejs-demo-app
