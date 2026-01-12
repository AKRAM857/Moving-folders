# 🚀 Cloud-Watchman: Automated Web Infrastructure

This project demonstrates a transition from manual server management to professional DevOps automation on AWS.

## 🏗 Phase 1: The Manual Bridge (Ubuntu/EC2)
In the first phase, I used an **AWS EC2 (Ubuntu)** instance to manually deploy my site.
- **Tools:** AWS CLI, Bash, Git.
- **Workflow:** I pushed code from VS Code to GitHub, then SSH'd into Ubuntu to run a `deploy.sh` script.
- **The Script:** This script performed a `git pull` followed by an `aws s3 sync` to update the website.

## 🤖 Phase 2: GitHub Actions Automation
I replaced the manual steps with a **CI/CD pipeline** to achieve "Zero-Touch" deployment.
- **The Robot:** Created a `.github/workflows/main.yml` file.
- **Security:** Stored AWS Access Keys in **GitHub Secrets** to keep them hidden.
- **Workflow:** Now, a single `git push` triggers GitHub to automatically update the S3 bucket and CloudFront cache.

## 🕵️ The Watchman (Uptime Monitor)
To ensure the site stays live, I repurposed my Ubuntu server as a 24/7 monitor.
- **Logic:** A Python script checks the site status every 10 seconds.
- **Logging:** All results are saved to `site_monitor_logs.csv` using a Linux `screen` session.