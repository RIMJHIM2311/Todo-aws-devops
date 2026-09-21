# AWS DevOps To-Do Application

Simple To-Do application for the AWS DevOps practical assessment.

## Features
- Add task
- Update task
- Mark task complete/incomplete
- Delete task
- Persistent JSON storage
- `/health` endpoint
- GitHub Actions deployment

## Run locally
```bash
npm install
npm start
```
Open http://localhost:3000

## AWS
Recommended directory: `/opt/todo-app`
```bash
npm ci --omit=dev
pm2 start server.js --name todo-app
pm2 save
```

## GitHub Secrets
Create `AWS_HOST`, `AWS_USER`, and `AWS_SSH_KEY` in Repository Settings -> Secrets and variables -> Actions. Never commit private keys.

## CI/CD
A push to `main` triggers GitHub Actions, which SSHs to EC2, updates the code, installs dependencies, restarts PM2, and runs a health check.

## Nginx
Reverse proxy ports 80/443 to `http://127.0.0.1:3000`. Do not expose port 3000 publicly.
