# Hosting Setup (Production Environment)
For my production environment, I deployed the website on DigitalOcean, using a WordPress Droplet created from the Marketplace. This satisfies the CP3402 requirement of hosting the site on a public cloud provider (AWS, Azure, Google Cloud, or DigitalOcean). The Droplet provides a stable, publicly accessible environment for the final site.
Why I chose DigitalOcean
I selected DigitalOcean because it offers:
A simple one‑click WordPress installation
Full SSH access for automated deployments
A clean Ubuntu environment without vendor‑specific restrictions
Easy integration with GitHub Actions
Predictable pricing and low resource usage
This allowed me to focus on theme development and workflow rather than server troubleshooting.
Droplet Configuration
Provider: DigitalOcean
Image: WordPress on Ubuntu (Marketplace)
Plan: Basic Droplet (1GB RAM)
Region: Sydney1
Access: SSH (root user)
Web stack: Apache, PHP, MySQL
Public URL: http://170.64.128.126
After deployment, I completed the WordPress installation through the browser and confirmed the site was externally accessible.
# Local Development Workflow (Using Docker + GitHub Desktop)
I built my local development environment using Docker, which allowed me to run WordPress in a consistent, containerised setup. This approach ensured that my local environment closely matched the production server, reducing compatibility issues.
Local Development Tools Used
Docker — to run WordPress, MySQL, and phpMyAdmin containers
GitHub Desktop — to manage commits, branches, and pushes
Visual Studio Code — to edit theme files and manage the repository
GitHub repository — containing my parent theme, child theme, README, and REPORT
Using Docker provided an efficient and reproducible workflow, while GitHub Desktop made version control simple and visual. Visual Studio Code served as my main development environment for writing PHP, CSS, and template files.
# Deployment Workflow (GitHub Actions)
To meet the CP3402 requirement for a professional deployment workflow, I implemented an automated deployment pipeline using GitHub Actions. This workflow updates the child theme on the production server whenever I push changes to the main branch.
Why deploy only the theme?
WordPress core and plugins should not be version‑controlled or deployed manually.
Instead, I deployed only:
My child theme
Custom templates
Custom CSS/JS
Theme functions
This follows industry best practices and keeps the workflow clean and maintainable.
How the workflow works
I generated an SSH key pair on my local machine.
I added the public key to the DigitalOcean Droplet.
I added the private key to GitHub as an encrypted secret.
I created a GitHub Actions workflow (deploy.yml) that:
Checks out the repository
Connects to the Droplet via SSH
Uses rsync to upload the child theme to:
/var/www/html/wp-content/themes/lifelong-learning-child>/
Deletes old files and replaces them with the latest version
Trigger 
The workflow runs automatically on:
Code
on:
  push:
    branches: [ "main" ]

This means every commit to main updates the live site instantly.
Benefits of this workflow
No manual FTP uploads
No logging into the server to update files
Ensures consistent, reproducible deployments
Reduces human error
Demonstrates a real DevOps‑style workflow suitable for industry
Security Considerations
To keep the server secure:
I used SSH keys instead of passwords
I ran apt update && apt upgrade to apply system updates
I restricted deployment to a single GitHub branch
I avoided storing credentials in the repository
I used GitHub encrypted secrets for sensitive data
