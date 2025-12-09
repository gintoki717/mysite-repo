# Static Website Hosting on AWS (S3 + CloudFront + CI/CD Pipeline)

This project demonstrates how to deploy a static website on AWS using **Amazon S3**, **CloudFront**, and a fully automated **CI/CD pipeline (GitHub → AWS CodePipeline → S3 → CloudFront)**.

It is designed as a real-world, production-ready architecture following AWS recommended best practices.

---

## 1. Project Overview

This project hosts a static website (HTML/CSS) on **Amazon S3**, served securely through **Amazon CloudFront** (CDN), and automatically deployed via an AWS-native **CI/CD pipeline**.

Whenever code is pushed to the GitHub repository, AWS CodePipeline automatically:

1. Detects the change from GitHub  
2. Packages the files  
3. Deploys them to the S3 bucket  
4. Makes the new version available through CloudFront

This eliminates manual uploads and ensures fast global distribution.

---

## 2. Architecture Diagram

<img width="1631" height="1110" alt="image" src="https://github.com/user-attachments/assets/d723575c-0f9f-4be7-8b51-db0dae5938c2" />



---

##  3. CI/CD Pipeline Flow

<img width="700" height="1401" alt="image" src="https://github.com/user-attachments/assets/238cbc28-261e-4d12-9655-345cc1525c85" />





---

##  4. Tech Stack

**AWS Services**
- Amazon S3 (Static Website Storage)
- Amazon CloudFront (CDN Distribution)
- Origin Access Control (OAC)
- AWS CodePipeline
- AWS IAM

**Tools**
- GitHub Repository
- GitHub Desktop (local version control)
- Visual Studio Code (development)

**Frontend**
- HTML  
- CSS  

---

## 5. Features

- **Private S3 bucket** using CloudFront OAC (no public access)
-  **Global CDN** powered by CloudFront
-  **Automated Deployment** using GitHub + CodePipeline
-  **No manual file uploads to S3**
-  CloudFront caching with optional manual invalidation
-  Automatic packaging via CodePipeline (mysite.zip)
-  Clean folder structure and professional workflow

---

##  6. Project Structure





This repo only contains static frontend files; all deployment is handled automatically via CodePipeline.

---

##  7. Deployment Workflow (Step-by-Step)

### **1. Commit & Push**
You update website files using VS Code, then commit & push using GitHub Desktop.

### **2. GitHub → CodePipeline Notification**
GitHub webhook notifies AWS CodePipeline that new code is available.

### **3. CodePipeline – Source Stage**
Fetches the GitHub repo and packages it into **mysite.zip**.

### **4. CodePipeline – Deploy Stage**
Extracts the ZIP into the root of the S3 bucket:

S3://your-bucket/index.html

S3://your-bucket/style.css



### **5. CloudFront Serves Content**
CloudFront retrieves updated files directly from the S3 bucket using OAC.

### **6. CDN Caching**
Content may be cached up to ~24h unless manually invalidated.

---

##  8. How to Trigger Deployment

Deployment is fully automatic.

Any of the following steps triggers the deployment：

- Push to `main` branch  
- Merge Pull Request into `main`  
- Manual "Release Change" in CodePipeline console  

---

##  9. Live Demo URL


https://d1d5zh1syg50np.cloudfront.net





---

##  10. Known Limitations / Notes

- CloudFront may serve cached content; use **Invalidation** to force refresh.
- CodePipeline deploys files into S3 root; ensure correct pipeline permissions.  
- ZIP in S3 is the packaged artifact, not the version served to users.

---

##  11. License
MIT License.

---

##  12. Author
gintoki717  
AWS Cloud / DevOps Enthusiast  
AWS Certified Solution Architect Associate

---

