## Deploying a Static Website with CI/CD using GitHub Actions

## Overview

This project demonstrates how to build and deploy a static website using GitHub Pages and CI/CD automation with GitHub Actions. Any time a change is pushed to the master branch, GitHub Actions will automatically build and deploy the site.

## Tech Stack
HTML / CSS: Frontend of the static site
GitHub Pages: Hosting service
GitHub Actions: CI/CD automation

## Folder Structure
```my-static-site/ 
   ├── index.html
   ├── style.css
   ├── .github/ │ 
       └── workflows/ │ 
           └── deploy.yml ```

## CI/CD Process (Step-by-Step)

1. Project Setup
mkdir my-static-site && cd my-static-site 

## Create your index.html and style.css inside the folder
2. Git and GitHub Setup
git init git remote add origin https://github.com/your-username/my-static-site.git 
Replace the URL with your actual GitHub repo

## 3. Create GitHub Actions Workflow
mkdir -p .github/workflows nano .github/workflows/deploy.yml 
Paste the following content into deploy.yml:
name: Deploy static content to GitHub Pages on: push: branches: [ "master" ] workflow_dispatch: permissions: contents: read pages: write id-token: write concurrency: group: "pages" cancel-in-progress: false jobs: deploy: environment: name: github-pages url: ${{ steps.deployment.outputs.page_url }} runs-on: ubuntu-latest steps: - name: Checkout code uses: actions/checkout@v4 - name: Setup Pages uses: actions/configure-pages@v4 - name: Upload static files uses: actions/upload-pages-artifact@v3 with: path: '.' - name: Deploy to GitHub Pages id: deployment uses: actions/deploy-pages@v4 

## 4. Commit and Push to GitHub
git add . git commit -m "Initial commit with CI/CD workflow" git push -u origin master 

## Deployment Result
GitHub Actions automatically builds and deploys your static website to GitHub Pages.
After the first successful run, your site will be live at:
https://your-username.github.io/my-static-site/ 

## Features
Automatic deployment on push
Clean and minimal setup
Hosted for free using GitHub Pages

License
This project is open-source and available under the MIT License.
Author
## Ankiambom Kelly
