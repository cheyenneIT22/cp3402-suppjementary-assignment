# Project Summary
This project involved designing, developing, and deploying a fully functional WordPress website using a custom child theme and a modern, industry‑aligned development workflow. The goal was to create a site that met the client’s content requirements while improving usability, structure, and visual presentation through thoughtful design and theme customisation.
Working individually, I was responsible for the entire development lifecycle — from planning and information architecture to theme development, cloud hosting, automation, and documentation. This required balancing technical implementation with design decisions to ensure the final site was accessible, responsive, and aligned with the client’s goals.
The project emphasised real‑world development practices, including version control, containerised local environments, automated deployment pipelines, and cloud‑based hosting. This approach ensured that the final product was not only functional but also maintainable, scalable, and professionally delivered.
# Skills and Technologies Developed (Employability Focus)
This project strengthened a wide range of technical and professional skills that are directly applicable to modern web development roles.
# Technical Skills
Docker for containerised local development, mirroring real production environments
Linux server administration, including SSH access, file permissions, and package management
DigitalOcean cloud hosting, including Droplet configuration and security hardening
Git & GitHub, using proper version control practices and GitHub Desktop for workflow efficiency
GitHub Actions, creating an automated CI/CD pipeline for theme deployment
WordPress theme development, including child theme structure, template overrides, and custom styling
PHP, HTML, CSS, and WordPress templating
Responsive design and accessibility improvements
Project management using Trello to track tasks, progress, and workflow stages
# Professional & Employability Skills
Ability to work independently and manage a full development lifecycle
Experience writing professional documentation (README, REPORT, deployment instructions)
Understanding of DevOps‑style workflows and automation
Problem‑solving in real server environments
Clear communication of technical processes for non‑technical audiences
Demonstrated ability to deliver a complete, production‑ready website
These skills reflect modern industry expectations and demonstrate my capability to work with real hosting environments, automated deployment pipelines, and collaborative development tools.
# Conclusion
This project provided valuable experience in full‑stack WordPress development, cloud hosting, and automated deployment workflows. By combining Docker, GitHub Actions, and DigitalOcean, I created a professional development environment that mirrors real industry practices.
The project strengthened my technical confidence, improved my workflow efficiency, and expanded my understanding of modern web development processes. Most importantly, it demonstrated my ability to independently deliver a complete, production‑ready website using contemporary tools and technologies — a key skillset for future roles in web development, DevOps, and digital production.

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
/var/www/html/wp-content/themes/u3a-child/
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
# Project Management and Development Workflow

Trello was used throughout the project as the primary project management and task organisation tool. The board provided a structured workflow for planning, tracking progress, and managing the different stages of website development. This helped ensure the project remained organised and aligned with the supplementary assignment requirements.

The Trello board was divided into several workflow columns to represent the development lifecycle:

To Do – tasks and assignment requirements that had not yet started
In Progress – features and pages currently being developed
Testing – completed tasks undergoing review, troubleshooting, or responsiveness testing
Completed – finished tasks that had been successfully implemented

Tasks were created and categorised based on major project components, including:

WordPress installation and configuration
Docker local development setup
GitHub repository setup and version control
Child theme creation and customisation
Home page development
About page development
Activities page development
Events page development
Gallery and media organisation
Navigation and footer structure
Responsive design improvements
DigitalOcean production deployment
GitHub Actions deployment automation
README and documentation creation
Testing and debugging

Trello was particularly useful for breaking the assignment into smaller, manageable development tasks. Each card contained notes, progress tracking, and reminders related to specific features or requirements. This supported time management and allowed development priorities to be clearly identified.

During development, Trello was also used alongside GitHub and Docker to coordinate workflow activities. For example:

Docker tasks tracked local environment configuration and troubleshooting
GitHub tasks tracked commits, repository updates, and deployment workflows
Website design tasks tracked page layouts, colour improvements, and image assets
Deployment tasks tracked production server setup using DigitalOcean

The use of Trello improved organisation and workflow efficiency by providing a clear visual overview of project progress. It also supported iterative development, where pages and features could be continuously refined, tested, and moved through the workflow process until completed.

Overall, Trello contributed to maintaining a structured and professional development process throughout the project lifecycle.