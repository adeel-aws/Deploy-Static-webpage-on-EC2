# 🌐 Automated Static Website Deployment

This project demonstrates a **fully automated static website deployment** on **AWS EC2** using **Terraform for infrastructure** and **GitHub Actions for CI/CD**.  
The website consists of an `index.html` and an `img` folder, automatically deployed and updated whenever changes are pushed to the repository.

---

## 🏗️ Project Overview

- **Static Website:** Simple HTML/CSS content  
- **Infrastructure as Code:** Terraform provisions EC2 instance  
- **CI/CD:** GitHub Actions automatically deploys website changes  
- **Web Server:** Nginx installed on EC2  
- **Automation:** Fully hands-off deployment and update process  

---

## 🗂️ Folder Structure

```text
project-root/
├── App/
│   ├── index.html            
│   └── img/                  
├── Terraform/
│   ├── main.tf              
│   ├── variables.tf          
│   ├── outputs.tf            
│   └── terraform.tfvars      
├── .github/
│   └── workflows/
│       ├── deploy.yml        
│       └── destroy.yml      
```

---

## ⚡ How It Works

1. **Terraform Infrastructure:**  
   - Creates an EC2 instance in AWS.  
   - Configures security groups for HTTP/SSH access.  
   - Outputs the EC2 public IP.

2. **GitHub Actions CI/CD:**  
   - Triggered on **push to main branch**.  
   - Runs Terraform init and apply automatically.  
   - Installs Nginx on the EC2 instance.  
   - Uploads `index.html` and `img` folder to the web server.  
   - Sets correct permissions for web access.

3. **Automatic Deployment Flow:**  
   - Push changes to GitHub → GitHub Actions triggers → Terraform provisions/updates EC2 → Website deployed → Live at EC2 IP.

---

## 📦 Features

- Fully automated static site deployment  
- Infrastructure as code with Terraform  
- Continuous deployment with GitHub Actions  
- Nginx web server setup included  
- Easy to update by simply pushing changes to `App/` folder  
- Reusable and scalable setup for future projects  

---

## 🛠️ Deployment Instructions

1. **Setup GitHub Secrets:**  
   - `AWS_ACCESS_KEY_ID`  
   - `AWS_SECRET_ACCESS_KEY`  
   - `EC2_KEY_PRIVATE` (private key to access EC2)

2. **Push Code to `main` Branch:**  
   GitHub Actions workflow will automatically:  
   - Apply Terraform changes  
   - Deploy website files to EC2  

3. **Access Website:**  
   - Use the EC2 public IP from Terraform outputs.  
   - Open `http://<EC2_PUBLIC_IP>` in a browser.

---

## 🔧 CI/CD Workflow (`deploy.yml`)

- Checks out the repo  
- Configures AWS credentials  
- Initializes and applies Terraform  
- Installs Nginx on EC2  
- Copies website files from `App/` to `/usr/share/nginx/html/`  
- Automatically updates website on every push

---

## ✅ Outcome

- Static website live on EC2  
- Infrastructure is codified and versioned  
- CI/CD ensures zero manual deployment steps  
- Ideal for practicing **DevOps, Terraform, and GitHub Actions**  

---

## ⚙️ Future Enhancements

- Add **SSL via ACM** and **HTTPS** support  
- Integrate **CloudFront CDN** for faster delivery  
- Add **monitoring and alerts** for EC2 uptime  
- Support multiple environments (dev, staging, prod)
