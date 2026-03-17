# Architecture Design Document (ADD)

Project Name: Aura – Interactive Menu

PlatformOrganization: minusJavaDocument

 Version: 1.0

 Status: Status: Design / Pre-Deployment

---

## Executive Summary

  This document outlines the purposed infrastructure architecture for a planned  demonstration environment of the Aura project.
   The objective is to provide a highly available, cost-effective, and performant hosting solution to showcase interactive, GSAP-animated digital menus to prospective cafe and restaurant clients. The architecture leverages **Amazon Lightsail** to minimize operational overhead while ensuring a secure and scalable foundation.

## System Overview

   The Aura demo environment will be hosted entirely within the *Amazon Web Services (AWS) cloud*, utilizing **Amazon Lightsail** as the primary compute and networking tier. This Virtual Private Server (VPS) model encapsulates the web server, application assets, and local storage into a unified, predictable environment. Continuous Integration and Continuous Deployment (CI/CD) pipelines will be established to ensure that the live demo reflects the latest source code.

## Infrastructure Components

| Component               | Technology              | Description / Justification |
|-------------------------|-------------------------|-----------------------------|
| Compute / Web Server    | Amazon Lightsail Instance (Ubuntu / Nginx)            | Serves as the core hosting environment. Nginx is selected for its lightweight footprint and high performance in serving static assets and handling concurrent connections, ensuring smooth playback of complex web animations.     |
| Network Identity        | Lightsail Static IP                      | Provides a persistent public IPv4 address. This guarantees that the demo URL remains functional and unchanged across server reboots or maintenance windows. |
| DNS Routing             | Amazon Route 53                          | Manages the custom domain routing (e.g., demo.minusjava.com) to the Static IP, providing a professional and branded access point for clients. |
| Security (Encryption)   | Lightsail Load Balancer / ACM            | Terminates SSL/TLS connections at the edge. Enforces HTTPS on Port 443 to secure data transit and build trust with end-users browsing the demo. |
| Storage                | Instance-Store SSD                       | Localized solid-state storage attached directly to the instance, minimizing latency when loading high-resolution food/beverage imagery and script files. |

## Security & Access Control

* **Firewall Configuration:** The instance is protected by the Lightsail perimeter firewall. Inbound traffic is strictly limited to HTTP (Port 80) and HTTPS (Port 443) for public access, and SSH (Port 22) restricted to authorized developer IP addresses only.
* **Encryption in Transit:** All client-server communication is encrypted using industry-standard TLS protocols.

## Backup & Disaster Recovery

* **Automated Snapshots:** Daily automated snapshots of the Lightsail instance are enabled. This creates full point-in-time image backups of the OS, configuration, and application data.
* **Recovery Objective:** In the event of a critical failure or a compromised deployment, the environment can be restored to a known healthy state within minutes directly from the snapshot registry.

## Deployment Strategy

The deployment lifecycle is fully automated to reduce manual overhead and human error:

* **Version Control:** Source code is maintained in a centralized GitHub repository
* **CI/CD Pipeline:** A GitHub Actions workflow will be configured to to listen for changes to the main branch.
* **Automated Delivery:** Upon a successful merge, the pipeline securely authenticates with the Lightsail instance via SSH and deploys the updated front-end assets directly to the Nginx web root directory.
