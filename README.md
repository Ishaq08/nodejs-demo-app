<img width="1858" height="957" alt="Screenshot from 2026-10-01 20-20-42" src="https://github.com/user-attachments/assets/3d16a582-4c0f-47d1-ab8c-f6762d6fd80d" /># nodejs-demo-app: CI/CD with GitHub Actions

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
<img width="1882" height="885" alt="Screenshot from 2026-10-01 20-20-10" src="https://github.com/user-attachments/assets/6be62114-8d61-4010-bac2-8df4cff07037" />

<img width="1858" height="957" alt="Screenshot from 2026-10-01 20-20-42" src="https://github.com/user-attachments/assets/a36584e8-7fee-4543-a0be-f65b116d2b9c" />


## Issues Faced and Fixed
Git asked for username and password on push: GitHub no longer accepts account passwords, so I used a Personal Access Token.
"Username and password required" in the Docker login step: the repository secrets were not added. Adding DOCKERHUB_USERNAME and DOCKERHUB_TOKEN fixed it.

##What I Learned
Coming from Jenkins: workflow file instead of Jenkinsfile, jobs instead of stages, runners instead of agents, and repository secrets instead of the Jenkins credentials store.
