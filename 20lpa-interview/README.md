# 20 LPA Interview Cracker — Deployment Guide

This repository contains the **20 LPA Interview Cracker** single-page study application, complete with a focus timer, analytics dashboard, theme customization, and study backup features.

Below are the instructions to run and deploy this application in different environments.

---

## 💻 1. Local Run (Zero Setup)
Since the app is a self-contained client-side single page app, you can run it without installing anything:
1. Double-click the [20lpa-interview-cracker.html](20lpa-interview-cracker.html) file to open it directly in any modern web browser.
2. Ensure browser local storage is enabled so your progress, notes, and stars are auto-saved.

---

## 🟢 2. Local Node.js Express Server
To run a local web server (useful to test routing or deploy to Node.js hosts):

### Prerequisites
*   Node.js (version 16 or higher) installed.

### Steps
1. Navigate to the project directory in your terminal.
2. Install the lightweight dependencies:
   ```bash
   npm install
   ```
3. Start the Express server:
   ```bash
   npm start
   ```
4. Open your browser and visit: `http://localhost:3000`

---

## 🐳 3. Docker Deployment
To run the application inside a containerized NGINX web server:

### Prerequisites
*   Docker installed.

### Steps
1. Build the Docker image:
   ```bash
   docker build -t 20lpa-interview-app .
   ```
2. Run the container, mapping port `80` to host port `8080`:
   ```bash
   docker run -d -p 8080:80 --name 20lpa-study-platform 20lpa-interview-app
   ```
3. Open your browser and visit: `http://localhost:8080`

---

## 🗲 4. Vercel Deployment
To deploy for free on Vercel:
1. Install Vercel CLI globally: `npm install -g vercel`
2. Run the login command: `vercel login`
3. Run the deploy command from the project root:
   ```bash
   vercel
   ```
4. Follow the command prompts (default settings are fully configured via `vercel.json`).

---

## 🟢 5. Netlify Deployment
To deploy for free on Netlify:
1. Install Netlify CLI: `npm install -g netlify-cli`
2. Run the deployment setup command:
   ```bash
   netlify deploy
   ```
3. Choose to create a new site and publish the current folder `.` (build and publishing settings are pre-configured via `netlify.toml`).

---

## 🐙 6. GitHub Pages
To host on GitHub Pages:
1. Push this directory to a public GitHub repository.
2. Go to repository **Settings** → **Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Choose the `main` (or `master`) branch and set the folder to `/ (root)`.
5. Save the configuration. GitHub will deploy your site to `https://<username>.github.io/<repo-name>/index.html` within a few minutes.
