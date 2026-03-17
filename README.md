# Aura---Digital-Menu-Architecture-🍽️✨
A Demo architecture diagram and plan for Aura - Digital Menu

Aura is a modern, interactive digital menu designed for cafes and restaurants. It delivers a visually engaging experience using smooth animations and responsive design, making it ideal for showcasing menu items to customers.

---

## 🚀 Project Overview

This project demonstrates a **cloud-based architecture** for hosting a live interactive menu using AWS services. It is designed as a **demo environment** to present the concept to potential clients while maintaining scalability for future production use.

---

## 🧱 Architecture

The system is designed using **Amazon Lightsail** as the core hosting environment, providing a simple and cost-effective VPS solution.

### 🔹 Key Components:

- **Compute / Hosting:** Amazon Lightsail (Ubuntu + Nginx)
- **Networking:** Static IP for consistent access
- **DNS Management:** Amazon Route 53
- **Security:** SSL/TLS via AWS Certificate Manager (ACM)
- **Storage:** Instance SSD (local storage)
- **CI/CD:** GitHub Actions for automated deployment
- **Backups:** Automated snapshots

> ⚠️ **Note:** For scalability and future production-readiness, optional components such as a load balancer, managed database, and object storage are included in the architecture but are not required for the initial demo deployment.

---

## 🖼️ Architecture Diagram

![ARCHITECTURE diagram.png](https://github.com/hazhl/Aura---Digital-Menu-Architecture-/blob/e04b24a6af04f6473c704d12519050461bf2b8d5/ARCHITECTURE%20diagram.png)

---

## ⚙️ Features

- 🎨 Interactive and animated UI (GSAP-based)
- ⚡ Fast performance with Nginx
- 🌐 Cloud-hosted demo environment
- 🔒 Secure HTTPS communication
- 🔄 Automated deployment pipeline
- 💾 Backup and recovery support

---

## 📦 Tech Stack

- **Frontend:** HTML, CSS, JavaScript (GSAP)
- **Backend:** ASP.net
- **Server:** Nginx (Ubuntu)
- **Cloud Provider:** AWS (Lightsail, Route 53, ACM)
- **CI/CD:** GitHub Actions

---

## 🔄 Deployment Strategy

1. Code is pushed to the main branch
2. GitHub Actions workflow is triggered
3. Application is deployed to the Lightsail instance via SSH
4. Nginx serves the updated files
