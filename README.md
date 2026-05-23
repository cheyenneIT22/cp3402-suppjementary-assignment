# Lifelong Learning Townsville

A Docker-based WordPress website developed for the CP3402 Supplementary Assignment.

The project demonstrates:
- local WordPress development using Docker
- Git version control
- GitHub Actions CI/CD workflows
- cloud deployment using DigitalOcean
- custom WordPress child theme development

---

## Project Overview

This website was designed for a community-focused lifelong learning organisation based in Townsville. 

The site promotes:
- educational activities
- social engagement
- community events
- lifelong learning opportunities

The design focuses on accessibility, responsiveness, and community engagement.

---

## Technologies Used

- WordPress
- Docker
- Docker Compose
- GitHub
- GitHub Actions
- DigitalOcean
- Visual Studio Code
- Astra Parent Theme
- Astra Child Theme

---

## Features

- Responsive WordPress website
- Custom child theme
- Docker local development environment
- Automated deployment pipeline
- Cloud-hosted production environment
- Community-focused design
- GitHub version control workflow

---

# Local Development Environment

The project was developed locally using Docker Desktop and Docker Compose.

The local environment included:
- WordPress container
- MySQL database container
- Visual Studio Code for development
- GitHub Desktop for version control

The site was accessed locally through:

```bash
http://localhost:8080
```

---

# Deployment

This project uses:
- Docker for local development
- DigitalOcean for production hosting
- GitHub Actions for automated deployment

Only the custom child theme is deployed through GitHub Actions.

---

## 1. Prerequisites

- DigitalOcean account
- WordPress Droplet
- GitHub repository
- Docker Desktop
- SSH access configured

---

## 2. Server Setup (DigitalOcean)

Create a WordPress Droplet from the DigitalOcean Marketplace.

SSH into the server:

```bash
ssh root@YOUR_SERVER_IP
```

Update the server:

```bash
apt update && apt upgrade -y
```

Confirm the WordPress themes directory:

```bash
cd /var/www/html/wp-content/themes
ls
```

---

## 3. Local Development (Docker)

Run WordPress locally using Docker Compose.

Example services:
- WordPress
- MySQL

Develop the child theme inside:

```bash
wp-content/themes/u3a-child
```

Use:
- Visual Studio Code for editing
- GitHub Desktop for commits and pushes

---

## 4. SSH Key Setup

Generate an SSH key locally:

```bash
ssh-keygen -t rsa -b 4096 -C "github-deploy"
```

Add:
- public key → DigitalOcean
- private key → GitHub Secrets

Required GitHub Secrets:

- SSH_PRIVATE_KEY
- SERVER_IP
- SERVER_USER
- THEME_DIR

---

## 5. GitHub Actions Workflow

Create:

```bash
.github/workflows/deploy.yml
```

Example workflow:

```yaml
name: Deploy Child Theme

on:
  push:
    branches: [ "main" ]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v3

    - name: Set up SSH
      uses: webfactory/ssh-agent@v0.7.0
      with:
        ssh-private-key: ${{ secrets.SSH_PRIVATE_KEY }}

    - name: Deploy child theme
      run: |
        rsync -avz --delete \
          ./your-child-theme-folder/ \
          ${{ secrets.SERVER_USER }}@${{ secrets.SERVER_IP }}:${{ secrets.THEME_DIR }}/u3a-child/
```

---

## 6. Deployment Workflow

1. Make changes locally using Docker
2. Commit changes using GitHub Desktop
3. Push to the `main` branch
4. GitHub Actions automatically deploys updates
5. The live WordPress child theme updates on the production server

---

# Production Environment

Production hosting was implemented using DigitalOcean.

The production environment included:
- Ubuntu Linux server
- WordPress installation
- SSH-based deployment
- GitHub Actions automation

---

# Author

Developed for CP3402 Supplementary Assignment.